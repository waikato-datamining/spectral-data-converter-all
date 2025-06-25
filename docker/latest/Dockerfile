ARG DOCKER_REGISTRY=public.aml-repo.cms.waikato.ac.nz:443/
FROM ${DOCKER_REGISTRY}ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
       git-core \
       wget \
       python3 \
       python3-dev \
       python3-venv \
       python3-pip \
       python3-pandas \
       python3-chardet \
       python3-full \
       build-essential \
       libglib2.0-0 \
       libsm6 \
       libxrender-dev \
       libxext6 \
       libgl1 \
       libglx-mesa0 \
       libpq-dev && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m venv /opt/spectral-data-converter && \
    /opt/spectral-data-converter/bin/pip --no-cache-dir install \
        git+https://github.com/waikato-datamining/spectral-data-converter.git \
        git+https://github.com/waikato-datamining/spectral-data-converter-sklearn.git \
        git+https://github.com/waikato-datamining/spectral-data-converter-vis.git

ENV PATH=/opt/spectral-data-converter/bin:$PATH
ENV NUMBA_CACHE_DIR=/tmp
ENV MPLCONFIGDIR=/tmp
COPY bash.bashrc /etc/bash.bashrc
WORKDIR /workspace

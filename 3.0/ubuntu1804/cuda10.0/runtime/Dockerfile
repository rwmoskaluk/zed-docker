FROM nvidia/cuda:10.0-base-ubuntu18.04

ENV NVIDIA_DRIVER_CAPABILITIES \
        ${NVIDIA_DRIVER_CAPABILITIES:+$NVIDIA_DRIVER_CAPABILITIES,}compute,video,utility

# Setup the ZED SDK
RUN apt-get update -y && apt-get install --no-install-recommends lsb-release wget less udev sudo -y && \
    wget -O ZED_SDK_Linux_Ubuntu18.run https://download.stereolabs.com/zedsdk/3.0/cu100/ubuntu18 && \
    chmod +x ZED_SDK_Linux_Ubuntu18.run ; ./ZED_SDK_Linux_Ubuntu18.run -- silent runtime_only && \
    rm ZED_SDK_Linux_Ubuntu18.run && \
    rm -rf /var/lib/apt/lists/*

# ZED Python API
RUN apt-get update -y && apt-get install --no-install-recommends python3 python3-pip -y && \ 
    wget download.stereolabs.com/zedsdk/pyzed -O /usr/local/zed/get_python_api.py && \
    python3 /usr/local/zed/get_python_api.py && \
    python3 -m pip install numpy opencv-python *.whl && \
    rm *.whl ; rm -rf /var/lib/apt/lists/*
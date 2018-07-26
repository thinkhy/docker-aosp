FROM openstf/aosp:jdk8


# Change source list to aliyun mirror sites
ADD sources.list /etc/apt/sources.list


RUN export DEBIAN_FRONTEND=noninteractive && \
    apt-get update && \
    apt-get -y install android-libselinux android-libselinux-dev

# Volumes for AOSP source
VOLUME ["/aosp"]
VOLUME ["/mirror"]

# Build commands must be run in the AOSP source tree
WORKDIR /aosp

# To handle the issue "USER: unbound variable"
ENV USER root

# Volume for external app source
VOLUME ["/app"]

# Volume for build artifacts
VOLUME ["/artifacts"]

# Set up entrypoint while working around docker/hub-feedback#811
ADD aosp.sh /usr/local/bin
#RUN ln -s /usr/local/bin/aosp.sh /aosp.sh

# Show help by default
CMD ["/aosp.sh", "--help"]

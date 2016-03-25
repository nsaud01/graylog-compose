FROM debian:jessie

MAINTAINER Micah Hausler, micah.hausler@ambition.com

ENV DEBIAN_FRONTEND noninteractive
ENV GRAYLOGWEB_VERSION 2.0.0-beta.1

RUN add-apt-repository ppa:openjdk-r/ppa
    apt-get update && \
    apt-get -y install \
    curl \
    dnsutils \
    git \
    htop \
    jq \
    less \
    man \
    net-tools \
    ntp \
    openjdk-8-jdk \
    pwgen \
    tzdata \
    unzip \
    vim \
    vim-common \
    wget \
    zip \
    && rm -rf /var/lib/apt/lists/*

ADD https://packages.graylog2.org/releases/graylog2-web-interface/graylog-web-interface-$GRAYLOGWEB_VERSION.tgz /opt/

RUN cd /opt/ \
    && tar xfz graylog-web-interface-$GRAYLOGWEB_VERSION.tgz \
    && mv graylog-web-interface-$GRAYLOGWEB_VERSION graylog \
    && rm graylog-web-interface-$GRAYLOGWEB_VERSION.tgz

EXPOSE 9443

WORKDIR /opt/graylog
CMD /opt/graylog/bin/graylog-web-interface -Dhttps.port=9443

# extend the official jenkins slave base image
FROM openshift/jenkins-slave-base-centos7

# specify wanted version of python
ENV PYTHON_VERSION 3.7.3

# install python
RUN set -x \
    && chown -R root:root /home/jenkins \
    && INSTALL_PKGS="gcc make openssl-devel wget bzip2-devel libffi-devel" \
    && yum install -y $INSTALL_PKGS \
    && cd /tmp \
    && wget https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tgz \
    && tar xf Python-${PYTHON_VERSION}.tgz \
    && cd Python-${PYTHON_VERSION} \
    && ./configure --enable-optimizations \
    && make altinstall \
    && cd .. \
    && rm -rf Python-${Python_VERSION} \
    && yum remove -y --setopt=tsflags=noscripts $INSTALL_PKGS \
    && yum clean all \
    && chown 1001:0 /home/jenkins

# switch to non-root for openshift usage
USER 1001
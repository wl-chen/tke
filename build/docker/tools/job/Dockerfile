FROM python:3.6-alpine
ENV HOME="/" \
    OS_ARCH="amd64" \
    OS_NAME="linux" \
    APP_VERSION="1.22.13"

RUN mkdir -p /tmp/kubectl/ && cd /tmp/kubectl && \
    if [ ! -f kubectl-$APP_VERSION-1-$OS_NAME-$OS_ARCH-debian-11.tar.gz ]; then \
      wget https://downloads.bitnami.com/files/stacksmith/kubectl-$APP_VERSION-1-$OS_NAME-$OS_ARCH-debian-11.tar.gz ; \
    fi && \
    export CHECKSUM=$(sha256sum kubectl-$APP_VERSION-1-$OS_NAME-$OS_ARCH-debian-11.tar.gz) && \
    echo "$CHECKSUM" | sha256sum -c - && \
    tar -zxf kubectl-$APP_VERSION-1-$OS_NAME-$OS_ARCH-debian-11.tar.gz -C /bin/ --strip-components=4 && \
    # apk add --update yum && \
    # wget https://kincos-1251707795.cos.ap-guangzhou.myqcloud.com/localpv/xfsprogs-5.9.0-8.tl2.x86_64.rpm && \
    # rpm -Uvh xfsprogs-5.9.0-8.tl2.x86_64.rpm && \
    rm -rf /tmp/kubectl && \
    # apk add --update rpm && \
    apk add --update findmnt && \
    apk add --update blkid && \
    # wget https://kincos-1251707795.cos.ap-guangzhou.myqcloud.com/localpv/xfsprogs-5.9.0-8.tl2.x86_64.rpm && \
    # rpm -ivh xfsprogs-5.9.0-8.tl2.x86_64.rpm --force --nodeps && \
    apk add --upgrade xfsprogs && \
    apk add --update curl && \
    apk add --no-cache bash && \
    rm -rf /var/cache/apk/*

ENTRYPOINT [ "kubectl" ]
CMD [ "--help" ]

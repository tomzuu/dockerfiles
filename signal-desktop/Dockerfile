FROM debian:sid

LABEL maintainer "tomzuu <toms@buu.lv>"

RUN apt-get update && apt-get install -y \
	libasound2 \
	libcanberra-gtk-module \
	fonts-roboto* \
	wget \
	gnupg \
	&& groupadd -g 1000 user && useradd -m -u 1000 -g user user \
	&& wget -4 https://updates.signal.org/desktop/apt/keys.asc \
	&& cat keys.asc | apt-key add - \
	&& echo "deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main" | tee -a /etc/apt/sources.list.d/signal-xenial.list \
	&& apt-get update && apt-get -y install signal-desktop

USER user

ENTRYPOINT ["/usr/local/bin/signal-desktop"]

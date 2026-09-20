FROM ghcr.io/home-assistant/base:latest

# Install python + pip
WORKDIR /srv
RUN \
  apk add --no-cache \
    python3 py3-pip py3-yaml git

# Prepare venv
RUN cd /srv && python3 -m venv venv

# Install modbus + py3yaml via pip
RUN cd /srv && source ./venv/bin/activate && \
    pip install \
      "git+https://github.com/sphings79/modbus-proxy@fix/exception-frame-mbap-length" \
      PyYAML


# Copy data for add-on
WORKDIR /
COPY run.sh /
WORKDIR /srv



RUN chmod a+x /run.sh
CMD [ "/run.sh" ]

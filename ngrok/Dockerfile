ARG BUILD_FROM
FROM $BUILD_FROM

# Copy root filesystem
COPY rootfs /

# Official ngrok agent v3 (Linux): https://ngrok.com/docs/guides/device-gateway/linux
ARG BUILD_ARCH
RUN set -x \
 && apk add --no-cache curl \
 && if [[ "${BUILD_ARCH}" = "aarch64" ]]; then ARCH="arm64"; fi \
 && if [[ "${BUILD_ARCH}" = "amd64" ]]; then ARCH="amd64"; fi \
 && if [[ "${BUILD_ARCH}" = "armhf" ]]; then ARCH="arm"; fi \
 && if [[ "${BUILD_ARCH}" = "armv7" ]]; then ARCH="arm"; fi \
 && if [[ "${BUILD_ARCH}" = "i386" ]]; then ARCH="386"; fi \
 && curl -fSL -o /tmp/ngrok.tgz "https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-${ARCH}.tgz" \
 && tar xzf /tmp/ngrok.tgz -C /bin \
 && rm -f /tmp/ngrok.tgz

# Initialize ngrok
RUN  ngrok --version

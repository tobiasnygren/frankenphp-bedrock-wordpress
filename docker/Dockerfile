FROM dunglas/frankenphp:1.0.3-php8.2

# install the PHP extensions we need (https://make.wordpress.org/hosting/handbook/handbook/server-environment/#php-extensions)
RUN install-php-extensions \
    bcmath \
    exif \
    gd \
    intl \
    mysqli \
    zip \
    imagick \
    opcache

COPY --from=wordpress /usr/local/etc/php/conf.d/* /usr/local/etc/php/conf.d/
COPY ./docker/caddy/Caddyfile /etc/caddy/Caddyfile
COPY --chown=root:root ./ /app/

CMD ["frankenphp", "run", "--config", "/etc/caddy/Caddyfile"]

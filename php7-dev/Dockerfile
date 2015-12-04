FROM php:7-apache
ADD apache2.conf /etc/apache2/apache2.conf
ADD symfony.ini /usr/local/etc/php/conf.d/symfony.ini

RUN apt-get update \
        && apt-get install -y libicu-dev \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo pdo_mysql opcache intl && a2enmod rewrite && mkdir /var/www/html/web

RUN pecl install -f xdebug-2.4 \
    && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20151012/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini
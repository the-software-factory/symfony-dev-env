FROM php:7.1.2-apache

# Install composer
RUN curl -L -o /usr/local/bin/composer https://getcomposer.org/download/1.3.3/composer.phar && \
    chmod +x /usr/local/bin/composer

# Install needed extensions
RUN apt-get update && \
    apt-get install zlib1g-dev -y && \
    pecl install apcu && \
    docker-php-ext-enable apcu && \
    docker-php-ext-install -j$(nproc) zip

# Modify apache configuration as needed
RUN sed -i "s|/var/www/html|/var/www/html/web|" /etc/apache2/sites-available/000-default.conf

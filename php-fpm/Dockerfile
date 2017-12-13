######
# See: https://hub.docker.com/_/php/
######

FROM php:7.2.0-fpm
MAINTAINER micooz <micooz@hotmail.com>

######
# You can install php extensions using docker-php-ext-install
######

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmagickwand-dev \
        libpng-dev \
        libtidy-dev \
        libpq-dev \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        libxslt-dev \
        cron \
        nano unzip \
    && docker-php-ext-install -j$(nproc) iconv pdo mbstring zip mysqli pdo_mysql tidy bcmath intl soap xsl \
    && docker-php-ext-configure gd \
        --with-gd \
        --with-freetype-dir=/usr/include/ \
        --with-png-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
    && pecl install redis imagick \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-enable imagick redis \
    && docker-php-source delete

#install nodejs
#RUN curl -sL https://deb.nodesource.com/setup_7.x | bash && apt-get install nodejs

# Install Composer
#RUN curl -s http://getcomposer.org/installer | php \
#    && mv composer.phar /usr/local/bin/ \
#    && echo "alias composer='/usr/local/bin/composer.phar'" >> ~/.bashrc

# Source the bash
#RUN . ~/.bashrc

# Clean up
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

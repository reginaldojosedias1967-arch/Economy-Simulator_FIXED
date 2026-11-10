FROM php:8.2-apache

# Copia todos os arquivos do repositório para o servidor
COPY . /var/www/

# Define a pasta pública correta (a pasta services contém o site)
ENV APACHE_DOCUMENT_ROOT /var/www/services
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# Habilita o carregamento do arquivo de conexão correto do Economy Simulator
RUN echo "auto_prepend_file = /var/www/services/2016-roblox-main/connect.php" > /usr/local/etc/php/conf.d/economy-globals.ini

EXPOSE 80

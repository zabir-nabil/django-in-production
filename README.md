# django-in-production


# Development

```
sudo python manage.py runserver 0.0.0.0:80
```

# Production


## Apache

```
cd /etc/apache2/sites-available
```

```
touch site_name.conf
```
## SSL

### Apache2 conf for SSL

~~~~
<VirtualHost *:80>
ServerName blog.nabil.info
ServerAlias www.blog.nabil.info
DocumentRoot "/var/www/nabil_site"
Alias /static /var/www/nabil_site/nabil_site/static/
WSGIScriptAlias / /var/www/nabil_site/nabil_site/wsgi.py
<Directory /var/www/nabil_site/>
    Order allow,deny
    Allow from all
</Directory>
</VirtualHost>

<VirtualHost *:443>
ServerName blog.nabil.info
ServerAlias www.blog.nabil.info
DocumentRoot "/var/www/nabil_site"
Alias /static /var/www/nabil_site/nabil_site/static/
WSGIScriptAlias / /var/www/nabil_site/nabil_site/wsgi.py
<Directory /var/www/nabil_site/>
    Order allow,deny
    Allow from all
</Directory>

    SSLEngine on
    SSLCertificateFile /var/www/certificate.crt
    SSLCertificateKeyFile /var/www/private.key
    SSLCACertificateFile /var/www/ca_bundle.crt

</VirtualHost>

~~~~

### HTTPS Redirect

```
pip install django-sslify # https://github.com/rdegges/django-sslify
```

### Run Apache Server

```
sudo service apache2 restart
```



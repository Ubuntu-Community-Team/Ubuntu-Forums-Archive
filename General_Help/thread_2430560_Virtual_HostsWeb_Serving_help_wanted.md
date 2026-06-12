---
title: "Virtual Hosts/Web Serving help wanted"
date: 2019-11-04
forum: General Help
---

### Post by jonr1111 on 2019-11-04
Hi all,
I have an Odroid running Ubuntu 18.04. It's currently running an instance of nextcloud (installed into /var/www/html) and it's also running pi-hole.
I access nextcloud at mydomain.com.
I want to install another self-hosted software package and I'd like to change my configuration so that I access nextcloud at nextcloud.mydomain.com and the new thing at newthing.mydomain.com.
I have set up a subdomain forward with my registrar and if I ping newthing.mydomain.com I see my public IP address returned - so that appears to be working.
I have created /var/www/newthing and placed a basic html file in it but going to newthing.mydomain.com  doesn't work. 
My virtual host file, in /etc/apache2/sites-available reads (comments removed);

```
<VirtualHost *:80>        ServerName mydomain.com
        ServerAlias www.mydomain.com
        ServerAdmin me@mydomain.com
        DocumentRoot /var/www/newthing
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
```

The contents of ports.conf is;

```
# If you just change the port or add more ports here, you will likely also# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf


Listen 80


<IfModule ssl_module>
	Listen 443
</IfModule>


<IfModule mod_gnutls.c>
	Listen 443
</IfModule>
```

When I try to access [http://newthing.mydomain.com](http://newthing.mydomain.com) it's getting redirected to http**s**://newthing.mydomain.com.
From memory, when I set up nextcloud this was also something I set up for security measures. But I can't really remember anything about it - I think it's a product of letsencrypt. I've tried changing my virtual hosts file for newthing to <VirtualHost *:**443**> but the result has been the same.

My sites-available directory contains:
000-default-le-ssl.com (contains the virtual host info for the nextcloud install)
000-default.conf
default-ssl.conf
new thing.mydomain.com.conf

My sites-enabled directory contains:
000-default-le-ssl.com
000-default.conf
new thing.mydomain.com.conf


Hoping someone can help.

Jon

---

### Post by TheFu on 2019-11-04
Don't use filenames with spaces.
I've never used an apache virtualhost file that short in my life.

ServerName needs to be on a line alone.

Isn't a
```
<Directory .....>

</Directory>
```
needed?

Also, the closing ```

  </VirtualHost>
```
is missing.

Please be very, very, careful making something like nextcloud available on the internet.  I run a nextcloud server, but require a VPN for any access from outside the LAN.

---

### Post by SeijiSensei on 2019-11-04
Apache selects virtual hosts based on the site's ServerName.  So the configuration file in sites-available needs to read
```

<VirtualHost *:80>
ServerName newthing.mydomain.com
DocumentRoot /var/www/newthing
[...]
<Directory /var/www/newthing>
     Options ...
     [any other needed directives]
</Directory>
</VirtualHost>

```

And as The Fu said, don't use directory or site names with embedded spaces, and close the virtual host container with </VirtualHost>.

Yes, you're using LetsEncrypt to create SSL encryption.  Once you have all the sites running properly on port 80, you can use certbot-auto to add an SSL certificate to newthing.mydomain.com.

---

### Post by jonr1111 on 2019-11-04
ok the spaces in the filename were just autocorrected on this post. The name of the new site is one word.
Also, </VirtualHost> is in the file too, I just didn't copy all of it.

OK, I have it running ok now. I had to add the subdomain to my SSL certificate.

---


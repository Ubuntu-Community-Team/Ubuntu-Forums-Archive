---
title: "Apache2 - creating virtual hosts"
date: 2005-04-04
forum: General Help
---

### Post by mandlnet on 2005-04-04
Hi,
Just new to ubuntu as of yesterday. I have got apache2, mysql, php etc working, but I do not understand how I create virtual servers etc using the sites-available and sites-enabled directories.

For example I want to be able to type [http://phpmyadmin/](http://phpmyadmin/) and go to the /var/www/phpmyadmin directory.

I have added phpmyadmin to my hosts file and that works fine, but every time I type [http://phpmyadmin/](http://phpmyadmin/) I get a directory listing of /var/www/

I tried installing webmin, but it would not let me log in using my username and password or the root username and password.

Any help is much appreciated.

Andrew

---

### Post by mandlnet on 2005-04-04
Never mind I have sorted it.

For those who are interested this is how.

I edited /etc/apache2/sites-available/default

Under the existing default virtual host I added the following:

```
<VirtualHost *>	
	ServerAdmin webmaster@localhost
	Servername phpmyadmin
	DocumentRoot /var/www/phpmyadmin
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/phpmyadmin>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>


	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

</VirtualHost>
```

Hope this helps

Andrew

---


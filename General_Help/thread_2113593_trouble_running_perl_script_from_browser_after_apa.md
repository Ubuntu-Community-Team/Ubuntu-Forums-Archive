---
title: "trouble running perl script from browser after apache2 install"
date: 2013-02-07
forum: General Help
---

### Post by brdohman on 2013-02-07
I am running Ubuntu 12.10. I followed this guide [https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts](https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts) to install apache on my system. All works well except running perl from the browser. After installation of apache, I have done the following

1 - installed ```
apt-fast install libapache2-mod-perl2
```
2 - Modified my virutalhost to look like so

```
<VirtualHost *:80>
	ServerAdmin my@email.com
	ServerName sub.domain.com

	DocumentRoot /var/www/sub.domain.com/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/sub.domain.com/public_html/api/v0
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

3 - ran ```
sudo chmod -R 755 api/
```

4 - restarted apache

5 - Opened up the browser to a directory the api/v0/createUser and all I see is the perl code. I'm not sure what I did wrong or if something more is missing. Code runs fine from the command line.

---


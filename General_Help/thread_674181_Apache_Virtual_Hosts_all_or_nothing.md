---
title: "Apache Virtual Hosts all or nothing"
date: 2008-01-21
forum: General Help
---

### Post by Jamina1 on 2008-01-21
HI!

I've searched endlessly on this topic and seen TONS of other people with the exact same problems that I am having. However, none of the solutions work. I have tried EVERYTHING to get Apache2 to see more than one virtual server to no avail.

Either all the virtual servers I create point to the default server or, they all resolve to 404.

What am I doing wrong?

I'm using Ubuntu 7.10 Server with Apache2 and Webmin.

This is the default setup, and I've added 2 additional "virtual sites" using webmin:
```

ServerName tecorg.testequipmentconnection.com
ServerAdmin webmaster@testequipmentconnection.org

	DocumentRoot /var/www/apache2-default
	<Directory "/var/www/apache2-default">
		Allow from all
	</Directory>	

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

```

```

<VirtualHost 65.161.131.156>
DocumentRoot "/var/www/skylinebroadcast.org"
ServerName skylinebroadcast.org
<Directory "/var/www/skylinebroadcast.org">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

```
<VirtualHost 65.161.131.156>
DocumentRoot "/var/www/testequipmentconnection.org"
ServerName testequipmentconnection.org
<Directory "/var/www/testequipmentconnection.org">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

Webmin automatically adds NameVirtualHost 65.161.131.156 to the end of the apache2.conf file.

Visiting ANY of the above sites drops me in /var/www/apache2-default, even if I put my other 2 domain names in my browser (both of which are pointed to this IP address)

I'm ripping my hair out here! What do I do?

---

### Post by four2theizz0 on 2008-01-27
hey man, jsut wondering if you have enabled the sites.  What i do is either put all of my vhost configs on one huge file or i make a separate config file for each domain.  where do you have this config stored?  i have mine stored in /etc/apache/sites-available.  Then you have to enable them by either just symlinking the files to /etc/apache/sites-enabled OR running a2ensite which will do the symlink for you.  That should solve your apache2-default problem.

edit - and then also restart apache after that :)

---

### Post by Jamina1 on 2008-01-27
> **four2theizz0 said:**
> hey man, jsut wondering if you have enabled the sites.  What i do is either put all of my vhost configs on one huge file or i make a separate config file for each domain.  where do you have this config stored?  i have mine stored in /etc/apache/sites-available.  Then you have to enable them by either just symlinking the files to /etc/apache/sites-enabled OR running a2ensite which will do the symlink for you.  That should solve your apache2-default problem.

edit - and then also restart apache after that :)

Yes! All 3 sites are enabled but apache only shows the first vhost to ALL the domains.

I figured it out though. My foldernames had .'s in them and removing them seemed to solve the problem.

---


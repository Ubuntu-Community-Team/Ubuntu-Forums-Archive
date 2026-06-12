---
title: "virtual host not working in ubuntu 14.10?"
date: 2015-03-12
forum: General Help
---

### Post by shamsat on 2015-03-12
I instaled the apache2 web server, the default web site for localhost from /var/www/html is worknig,
i want to add virtual host example.com to the apache2 web server, i created the folder /var/www/example.com and put the index.html in this folder, then add the /etc/apache2/sites-available/example.com.conf and run the command a2ensite to enable the website. now when want to open the example.com in the firefox it take me to the defualt localhost page in the /var/www/html
i can ping the example.com and that is working:
> 
ping example.com
PING example.com (10.158.157.147) 56(84) bytes of data.
64 bytes from example.com (10.158.157.147): icmp_seq=1 ttl=64 time=0.065 ms
64 bytes from example.com 10.158.157.147(): icmp_seq=2 ttl=64 time=0.047 ms
64 bytes from example.com (10.158.157.147): icmp_seq=3 ttl=64 time=0.047 ms
^C
--- example.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.047/0.053/0.065/0.008 ms

this is the example.com.conf:
```

<VirtualHost *:80>
	ServerAdmin user@localhost

	DocumentRoot /var/www/example.com
        ServerName  example.com
	<Directory />
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Require all granted
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Require all granted
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


```

---

### Post by dragonfly41 on 2015-03-12
This might help .. (taken from my working virtualhosts)


[LIST]
[*]In /etc/apache2/sites-available/example.com.conf 
[/LIST]

```

...
ServerName example.com
ServerAlias www.example.com
...

```

then apply a2ensite ..


[LIST]
[*]In /etc/hosts 
[/LIST]

```

127.0.0.1 localhost
127.0.1.1 example.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


Then restart apache2 .. sudo service apache2 restart

Browse to [http://example.com](http://example.com) or [http://www.example.com](http://www.example.com)

Perhaps also Ctrl + F5 to clear browser cache.

[later edit]

Also check ownership of /var/www/*  .. since apache2 expects www-data. Add your user id to www-data group.

---

### Post by shamsat on 2015-03-12
Thanks for reply i did that and now the virtual host work.

---


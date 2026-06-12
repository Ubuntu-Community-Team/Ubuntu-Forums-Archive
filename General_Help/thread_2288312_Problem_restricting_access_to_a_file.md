---
title: "Problem restricting access to a file"
date: 2015-07-26
forum: General Help
---

### Post by peter1897 on 2015-07-26
I am trying to protect the phpmyadmin login page with additional authentication with .htaccess password file. I created the password file .htpasswd in the directory /etc/phpmyadmin:

```
max@ubuntu:/etc/phpmyadmin$ ls -la | grep .htpasswd
-rw-r--r--  1 root root       42 Jul 26 11:12 .htpasswd
```

But is it possible to restrict users without admin rights to view the content of the file? The permission for **others** on the file must be **read** other wise it will not work. But with that permission other users can view the content of the file. 
If i set the permission for **others** to **0** i get **500 server internal error** when i try to access the phpmyadmin login page. Also if i move the file to my home directory which also have permission **0** for **others** i get the same error.

---

### Post by Lars Noodén on 2015-07-26
The default user for the web server is www-data.  So if that user can read the file then that is enough.  You can set the file to user:group root:www-data and permissions 640 and that should then work.

---

### Post by peter1897 on 2015-07-26
Thanks, it's working.

---

### Post by peter1897 on 2015-07-26
Is it possible to install self signed certificate only for the phpmyadmin, so only these users that are login to phpmyadming to receive prompt to trust the key?

---

### Post by Lars Noodén on 2015-07-26
Yes.  HTTPS is really served out of a second virtual host, that host might or might not have the same DocumentRoot as another HTTP virtual host.  If it does then the illusion that it is the same site is passed on to the visitor.  So you could phpmyadmin on just the HTTPS virtual host and block those directories on the HTTP virtual host.  Or you could use a different DocumentRoot all together for the HTTPS site if the content is not to be the same.

---

### Post by peter1897 on 2015-07-26
I am trying to do this on virtual machine but so far it doesn't work.
I created new virtual host file in /etc/apache2/sites-available/pma.conf and this is the content of the file:

```
<VirtualHost *:443>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /usr/share/phpmyadmin
        ServerName 192.168.56.105:443
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```

Then i run the command that creates the certificate and for Common Name i entered the ip of the virtual machine which is 192.168.56.105. But now if i try to access phpmyadmin page from my host machine on [https://192.168.56.105/phpmyadmin/](https://192.168.56.105/phpmyadmin/) i get "The connection has timed out"

What can be the reason for this error?

---

### Post by Lars Noodén on 2015-07-26
Did you then enable the site using [a2ensite](http://manpages.ubuntu.com/manpages/trusty/en/man8/a2ensite.8.html) so that something is there to listen on port 443?

---

### Post by peter1897 on 2015-07-26
My mistake, port 443 was blocked by the firewall, i open it and was able to connect to phpmyadmin. So, i guess my settings are correct.

---

### Post by peter1897 on 2015-07-26
I installed wordpress but for some reason the admin panel login is extremely slow. In which logs i have to look to see if this is not an apache or mysql issue or may be activating the ssl is causing this?

---

### Post by Lars Noodén on 2015-07-26
You mentioned trying to do this in a virtual machine.  There is a lot of overhead right there.  I don't know the real numbers but some years ago I read someone knowledgeable claim that about 40% is lost in  virtualization.  You could try watching with [top](http://manpages.ubuntu.com/manpages/trusty/en/man1/top.1.html) or [atop](http://manpages.ubuntu.com/manpages/trusty/en/man1/atop.1.html) in a terminal on the VM guest and another on the VM host while loading the HTTPS pages to see if anything spikes.  But I'm not sure that top polls often enough so you might have to try several times to see anything.  My (uneducated) guess would be that the combination of VM + SSL is creating a little lag.

---

### Post by peter1897 on 2015-07-26
I have now ssl enabled only for phpmyadmin login page but wordpress is still loading slow. I also installed mybb forum on the virtual machine but it is loading fine. 
Something interesting is that on the wordpess site the links to posts, categories and others are loading fine, but inside the dashboard, it loads slow also when i click the links Appearance, Plugins, Settings:

```
http://192.168.56.105/wordpress/wp-admin/themes.php
http://192.168.56.105/wordpress/wp-admin/options-general.php
http://192.168.56.105/wordpress/wp-admin/plugins.php
```

And when i click Add New to add a plugin i get this error:
```
An unexpected error occurred. Something may be wrong with WordPress.org or this server’s configuration. If you continue to have problems, please try the support forums.
```

I think this problem is related only to wordpress but i don't know what is causing it. I also reinstalled wordpress, it's the latest version, and also recreated the database but no change.

---

### Post by Lars Noodén on 2015-07-26
You could watch the logs live while you try that and see what the exact error message is.  

```

tail -f /var/log/apache2/error.log

```

Just taking a guess it might be that WordPress is expecting to write to a directory.  I'm not current on WordPress but you might be able to download manually instead, it's not a good idea to leave any directories that PHP can write to, which might be what it is expecting.

---

### Post by peter1897 on 2015-07-26
These are some of the errors from the apache log:
```
[Sun Jul 26 21:39:38.376072 2015] [:error] [pid 19359] [client 192.168.56.1:53635] PHP Warning:  stream_socket_client(): php_network_getaddresses: getaddrinfo failed: Name or service not known in /var/www/wordpress/wp-includes/class-http.php on line 1008, referer: http://192.168.56.105/wordpress/wp-admin/plugin-install.php
[Sun Jul 26 21:39:38.388291 2015] [:error] [pid 19359] [client 192.168.56.1:53635] PHP Warning:  stream_socket_client(): unable to connect to ssl://api.wordpress.org:443 (php_network_getaddresses: getaddrinfo failed: Name or service not known) in /var/www/wordpress/wp-includes/class-http.php on line 1008, referer: http://192.168.56.105/wordpress/wp-admin/plugin-install.php
[Sun Jul 26 21:39:38.397001 2015] [:error] [pid 19359] [client 192.168.56.1:53635] PHP Warning:  An unexpected error occurred. Something may be wrong with WordPress.org or this server’s configuration. If you continue to have problems, please try the <a href="https://wordpress.org/support/">support forums</a>. (WordPress could not establish a secure connection to WordPress.org. Please contact your server administrator.) in /var/www/wordpress/wp-includes/update.php on line 457, referer: http://192.168.56.105/wordpress/wp-admin/plugin-install.php
[Sun Jul 26 21:40:18.500830 2015] [:error] [pid 19359] [client 192.168.56.1:53635] PHP Warning:  stream_socket_client(): php_network_getaddresses: getaddrinfo failed: Name or service not known in /var/www/wordpress/wp-includes/class-http.php on line 1008, referer: http://192.168.56.105/wordpress/wp-admin/plugin-install.php
[Sun Jul 26 21:40:18.508552 2015] [:error] [pid 19359] [client 192.168.56.1:53635] PHP Warning:  stream_socket_client(): unable to connect to tcp://api.wordpress.org:80 (php_network_getaddresses: getaddrinfo failed: Name or service not known) in /var/www/wordpress/wp-includes/class-http.php on line 1008, referer: http://192.168.56.105/wordpress/wp-admin/plugin-install.php


```

---

### Post by Lars Noodén on 2015-07-26
Ok.  You'll probably want to ask in a new thread about WordPress.  There are some people here that use it quite a bit and will recognize the error and know the solution.  I'm not so current on WordPress.

---

### Post by peter1897 on 2015-07-26
The problem was in the virtual machine. I made some changes in the network adapters and forget to restart it, so it didn't have access to internet. I restarted the machine and now wordpress is loading fine. Probably some files like wp-includes/update.php that need access to internet have been the reason for the slow loading.

---


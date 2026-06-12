---
title: "403 Forbidden and client denied by server configuration in Apache 2.2.2"
date: 2014-04-23
forum: General Help
---

### Post by kabeza on 2014-04-23
Hi
I've installed lamp. Then I copied some sites from a backup and begun getting access problems in some files, so I did:
[LIST]
[*]created a new group www and added my user to it, then logout->login
[*]set a sudo chown www-data:www on everything under /var/www
[*]set a chmod with the following commands
[/LIST]

```

sudo find /var/www -type f -exec chmod 664 {} \;
sudo find /var/www -type d -exec chmod 775 {} \;
sudo find /var/www -type d -exec chmod g+s {} \;

```

[IMG]http://i.stack.imgur.com/V6TeQ.png[/IMG]

As you can see in the image I still couldn't solve the problem. Opened apache error.log and saw

```
[error] [client 127.0.0.1] client denied by server configuration: /var/www/abril/application/views/tplcan/css/font-awesome.min.css
```

After some google and reading, opened /etc/apache2/sites-enabled/000-default and put this

```
<VirtualHost *:80>
    ServerName 127.0.0.1
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    <Directory /var/www>
        DirectoryIndex index.php
        AllowOverride All
        # Apache 2.2
        Order allow,deny
        Allow from all
        # Apache 2.4
        #Require all granted
    </Directory>
</VirtualHost>
```

Restarted server. Tried also with the Require all granted line, restarted, but didn't work (of course bc I have 2.2.2 and Require all granted is for 2.4)

Any ideas?

Thanks a lot in advance

---


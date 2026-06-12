---
title: "Problems with Wordpress using apt-get"
date: 2013-04-29
forum: General Help
---

### Post by derrend on 2013-04-29
64-bit ubuntu 12.10:-

I cannot get Wordpress to work when installed through apt-get,
I follow the guide here [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) and everything is fine until it becomes time to install a plugin,

I install vsftpd and make sure local connections are allowed but when I enter my ftp information after being prompted by wordpress I get "Could not create directory. /srv/www/wp-content/localhost/upgrade" so I enter the ftp info for root and get "Username/Password incorrect for root" which is a lie because they are correct.

So I then try to change the owner of all files under '/var/www/wordpress' to 'www-data' but still get "Could not create directory. /srv/www/wp-content/localhost/upgrade",
so then just for the heck of it I 'chmod -R 777 /var/www/wordpress /srv' but still amazingly and even after restarting the services and then rebooting the server itself I still get "Could not create directory. /srv/www/wp-content/localhost/upgrade"

Please can anyone suggest where I might be going wrong, and please no advice regarding "Don't use apt-get" because I'm sure it wouldn't be in the default repos if it was broken, also I would like to use apt-get for neatness.

Please help :)

---

### Post by kamranm1200 on 2013-04-29
Maybe this article might help you. Here's the link: [http://ubuntuarena.wordpress.com/networking-3/how-to-install-lamp-linux-apache-mysql-php-on-ubuntulinux-mint/](http://ubuntuarena.wordpress.com/networking-3/how-to-install-lamp-linux-apache-mysql-php-on-ubuntulinux-mint/)

It tells you how to install the LAMP stack, but it will help you to get a web server running so you can use WordPress.

This article might help you as well, as it tells you how to install WordPress on Ubuntu: [https://www.digitalocean.com/community/articles/how-to-install-wordpress-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-install-wordpress-on-ubuntu-12-04)

Let me know if any of these articles help! :)

---

### Post by derrend on 2013-04-29
Thanks very much for the suggestions but that guide instructs on how to install wordpress outside of apt-get which I'm trying to avoid, reason being that this server is for a friend and I'd like them to be able to keep their software up to date easily. I did see a comment at the bottom of the second guide though - "[COLOR=#111111][FONT=Helvetica Neue]Most people have you use apt-get, but the permissions end up all wonky and this was so much more straight forward." so the problem I'm having doesn't seem uncommon.

The reason I also set the permissions to 777 on the directories was to get wordpress to create a folder so then i could see the name of the user it used, which obviously hasn't worked yet. Any other ideas how I might be able to debug this?

Thanks again :)[/FONT][/COLOR]

---


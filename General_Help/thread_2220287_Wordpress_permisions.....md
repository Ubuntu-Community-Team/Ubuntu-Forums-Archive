---
title: "Wordpress permisions...."
date: 2014-04-27
forum: General Help
---

### Post by saur02 on 2014-04-27
Hi, this is driving me nuts, I have installed wordpress on server 14.04
 
in /var/www/html there is a symlink wordpress -> /usr/share/wordpress

when I browse to [http://mysite.com/wordpress](http://mysite.com/wordpress) I can see the site, and log in, but I am unable to update or add any plugins. When I try to install one I get the following...

> [COLOR=#444444][FONT=Open Sans]Downloading install package from [/FONT][/COLOR][COLOR=#444444][FONT=Consolas]https://downloads.wordpress.org/plugin/wordfence.5.0.4.zip[/FONT][/COLOR][COLOR=#444444][FONT=Open Sans]…[/FONT][/COLOR][COLOR=#444444][FONT=Open Sans]Unpacking the package…[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]Could not create directory.[/FONT][/COLOR]

I have followed [this guide]("https://www.digitalocean.com/community/articles/how-to-configure-secure-updates-and-installations-in-wordpress-on-ubuntu") and created a user called wp-user, I have set the ownership of all the files (including the symlink, and everything below) to wp-user:www-data and I have set the permissions to 755, I have tried changing the plugins folder to 777 and owned by www-data but that doesn't make any difference. I am able to log in with wp-user and create and delete files and directory.  

I'm sure i'm missing something obvious but cant work out what it is.....

---

### Post by saur02 on 2014-04-27
I've just created a "upgrade" directory in "wp-content" as there wasn't one. But its still not working...

i've tried changing everything in the wordpress directory to 777 and still get the same "unable to create directory" message!

---

### Post by SeijiSensei on 2014-04-27
Are you use you used the "-R" ("recursive") switch when you changed ownerships and permissions so the changes will "trickle down" the entire directory tree?
```

cd /usr/share
sudo chown wp-user:www-data -R wordpress
sudo chmod 770 -R wordpress

```
I remove all privileges for users other than wp-user and www-data, so I use 770 for chmod.

Overall I take a somewhat different approach from you and put the www-data user into wp-user's group.  The easiest way to do that is add "www-data" to the end of the entry for wp-user in /etc/group like this:
```

wp-user:x:1001:www-data

```

---


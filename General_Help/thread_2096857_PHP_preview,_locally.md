---
title: "PHP preview, locally"
date: 2012-12-21
forum: General Help
---

### Post by TheNavigator on 2012-12-21
Hello there guys. I'm a pretty old user of linux, however, I still need some help. LOL

I need something easy to preview my PHP work, I guess Dreamweaver does that. Is there any kind of software for doing that? Or must I install apache and PHP5 locally to do it? Is there a "simpler" way?

---

### Post by Kljuka on 2012-12-21
I don't understand what you need: Do you need a text editor to edit the source of your php code or do you need a LAMP server to view the result of your interpreted code (the result)?

If you need a text editor, there are really many to use:
- The shell ones: Vi, Vim, Emacs, ...
- Graphical ones: Gedit, Bluefish, ...

If you need LAMP server (Linux, apache, php and mysql), it is really easy to install it. Just 2 commands:
```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

---

### Post by superdaveozzborn on 2012-12-21
```
sudo apt-get install lamp-server^
```

I think is the correct command for installing LAMP in ubuntu

---

### Post by TheNavigator on 2012-12-22
> **Kljuka said:**
> I don't understand what you need: Do you need a text editor to edit the source of your php code or do you need a LAMP server to view the result of your interpreted code (the result)?

If you need a text editor, there are really many to use:
- The shell ones: Vi, Vim, Emacs, ...
- Graphical ones: Gedit, Bluefish, ...

If you need LAMP server (Linux, apache, php and mysql), it is really easy to install it. Just 2 commands:
```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```
Well, yes actually, the LAMP server.

A last question, can LAMP be configured so that the default location is user-configured instead of a specified directory and copying the files every few seconds?

---

### Post by mcduck on 2012-12-22
> **superdaveozzborn said:**
> ```
sudo apt-get install lamp-server^
```

I think is the correct command for installing LAMP in ubuntu

both work just as well.

The only issue with tasksel is that it shouldn't, at the moment, be used to remove any tasks from the system. But using it to install things is perfectly fine.

---

### Post by mcduck on 2012-12-22
> **TheNavigator said:**
> Well, yes actually, the LAMP server.

A last question, can LAMP be configured so that the default location is user-configured instead of a specified directory and copying the files every few seconds?

Yes, you can configure Apache to use any directory you want as it's document root (or of course even multiple directories if you want to use virtual hosts to handle many websites from the same machine). Or you can enable user directories, which gives each user on the computer their own www directory.

For development work I usually disable Apache's default site and create a new one that uses a directory inside my home as it's document root.

---

### Post by SeijiSensei on 2012-12-22
Just make sure that the Apache user, "www-data", can read and list the directory in which the web site resides.  If your home directory has the default 700 permissions, then the Apache user will be blocked.  Change /home/username to 711, and make sure either that the web directory is assigned to grop www-data, or that the files in that directory are world-readable.

If you are trying this out on a machine without exposure to the Internet, I'd just put the site in /var/www for simplicity, and use [http://localhost/](http://localhost/) as the default URL.

---

### Post by psychotix on 2012-12-22
I do alot of drupal dev and this is typically what I do when I setup a new site(vhost).

All my sites are in my home directory (/home/myuser/www/mysite)

1. Add files to /home/myuser/www/mysite

2. create vhost

file: /etc/apache2/sites-available/mysite

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/myuser/www/mysite

	ServerName mysite.dev
	ServerAlias mysite.dev
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	ErrorLog /var/log/apache2/mysite.error.log
	CustomLog /var/log/apache2/mysite.access.log combined
</VirtualHost>



3. add entry to hosts file

127.0.0.1   mysite.dev

4. enable site

$> sudo a2ensite mysite
$> sudo service apache2 restart


If that all works you can go to "mysite.dev" in your browser and it will load your site assuming you have an index file.

---


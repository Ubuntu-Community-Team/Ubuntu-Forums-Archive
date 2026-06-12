---
title: "Apache2 help- unable to open site locally"
date: 2022-12-14
forum: General Help
---

### Post by stevermann on 2022-12-14
I have a program (Mediawiki) that uses the web as its front-end.  The web page is in /var/www/html/mediawiki/index.php.

From another computer on my local network, I can get into the site by entering in my browser "http://192.168.1.187/mediawiki". Works just fine.
But, I cannot get into the site from the computer that is hosting the Mediawiki site (Ubuntu 20.04 desktop).

When I enter "http://192.168.1.187" into either computer's browser, I get the [I]Apache2 Default Page - It works.

[/I]Any ideas where I should be looking?

---

### Post by dragonfly41 on 2022-12-15
/etc/hosts    ????

---

### Post by ActionParsnip on 2022-12-15
is apache accepting connections from anything but localhost? Sounds likely
In httpd.conf look for the "Listen" line and change it to
```

Listen 80

```
I suspect yours says
```

Listen 127.0.0.1:80

```
or similar

---

### Post by ActionParsnip on 2022-12-15
Onbiously with any config file, make a backup copy to allow easy roll back. Possibly
```

sudo cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf-2022-12-15-01

```

to restore, simply cat over the top
```

cat /etc/httpd/conf/httpd.conf-2022-12-15-01 | sudo tee /etc/httpd/conf/httpd.conf > /dev/null

```
Then restart your service

---

### Post by stevermann on 2022-12-15
Thanks for the inputs.
I should have added that I am trying to mirror a working system. The working system is running Ubuntu 18.04 desktop and the mirror is running Ubuntu 20.04 desktop.
On the working system, I can log on to <ip>/mediawiki using a browser on that computer as well as any browser on that LAN.
On the mirror system, I can log on to <ip>/mediawiki using any browser on the LAN, but *not *using a browser on the mirror computer.

On the suggestions so far:
/etc/hosts are identical except for the hostname.

httpd.conf: curiously, neither system has an httpd.conf file, or even an /etc/httpd directory.

---

### Post by ActionParsnip on 2022-12-15
Well, wherever Ubuntu puts httpd.conf or it's config file for apache

---

### Post by SeijiSensei on 2022-12-15
> **stevermann said:**
> When I enter "http://192.168.1.187" into either computer's browser, I get the [I]Apache2 Default Page - It works.

[/I]Any ideas where I should be looking?
The default page is stored in /var/www/html as referenced by the "DocumentRoot" directive in /etc/apache2/sites-available/000-default.conf. 

The URI /mediawiki would thus point to a directory under /var/www/html. So one solution to your problem might be to create a /var/www/html/mediawiki directory and copy the contents of the directory you want the server to use there. You'll need to be root with sudo to do this.

Another, more complicated, option if you want to keep the mediawiki software stored in its current location would be to edit /etc/apache2/sites-available/000-default.conf and add
```

Alias /mediawiki   /path/to/where/mediawiki/is/stored
<Directory "/path/to/where/mediawiki/is/stored">
Require all granted
</Directory>

```
Then the server will match [http://192.168.1.187/mediawiki](http://192.168.1.187/mediawiki) to this declaration and use the software at "/path/to/where/mediawiki/is/stored".

After doing any of these things you'll need to restart the Apache server with the command
```
systemctl restart apache2
```

---

### Post by stevermann on 2022-12-15
"[COLOR=#000000]So one solution to your problem might be to create a /var/www/html/mediawiki directory"


[/COLOR]Thanks, but that is already where the mediawiki web files are located:
/var/www/html/mediawiki.index.php


Remember, my problem is: I can access the mediwiki web pages from any browser on the LAN, but not from the computer where Apache is running.

---

### Post by SeijiSensei on 2022-12-15
What if you use [http://localhost/mediawiki?](http://localhost/mediawiki?)

---

### Post by stevermann on 2022-12-15
The problem turns out to be the browser. I installed the Epiphany browser and local website access works just fine.
Thanks for the tips.

---


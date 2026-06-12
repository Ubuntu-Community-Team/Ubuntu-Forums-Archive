---
title: "Apache 2, PhpMyAdmin, MySQL not listed in menus"
date: 2008-06-21
forum: General Help
---

### Post by DougAlder on 2008-06-21
I'm running Hardy with Gnome Desktop. I probably should have installed the server version but i didn't so I used apt-get, as root, to install PhpMyAdmin which in turn installed Apache 2 and MySQL 5. However, no where in any of the Gnome menus can I find the apps and when I use Firefox 3 to browse to the PhpMyAdmin folder /usr/share/phpmyadmin and try to open index.php Firefox has no clue what to do with it. All i want to do is get a copy of my live site working locally so i can make create a better site. I thought it might be a permissions problem but i opened a terminal su to root then used gksu to open Firefox and still had the same problem. Any and all help appreciated

---

### Post by balagosa on 2008-06-24
hi, if i get your problem right, then you can not even access "phpmyadmin"? To do so, open up firefox. type in **localhost/phpmyadmin** at adress bar.

---

### Post by wdaniels on 2008-06-24
Like balagosa said, you have to access it via http otherwise there is no web server acting to process and serve the file. The reason you can browse local plain HTML files using the file:// scheme is because they don't need any pre-processing.

---

### Post by DougAlder on 2008-06-24
I tried that and got 

> Not Found

The requested URL /phpmyadmin was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at localhost Port 80

---

### Post by wdaniels on 2008-06-24
Try:

```
sudo a2ensite default
```

---

### Post by DougAlder on 2008-06-24
> **wdaniels said:**
> Try:

```
sudo a2ensite default
```

got

> root@doug-laptop:/home/doug# sudo a2ensite default
This site is already enabled!
root@doug-laptop:/home/doug# 

---

### Post by undertakingyou on 2008-06-24
Sometimes after you install apache and then php you need to restart.  I had to.  After that the php stuff worked.

---

### Post by DougAlder on 2008-06-24
> **undertakingyou said:**
> Sometimes after you install apache and then php you need to restart.  I had to.  After that the php stuff worked.

I've restarted numerous times :(

---

### Post by wdaniels on 2008-06-24
Seems strange - I installed the phpmyadmin package on two machines just in the last couple of weeks and it all got configured fine automatically. Let's see the output of:

```
cat /etc/apache2/conf.d/phpmyadmin.conf
```

---

### Post by DougAlder on 2008-06-24
> **wdaniels said:**
> Seems strange - I installed the phpmyadmin package on two machines just in the last couple of weeks and it all got configured fine automatically. Let's see the output of:

```
cat /etc/apache2/conf.d/phpmyadmin.conf
```

Well that's interesting - 

> root@doug-laptop:/home/doug# cat /etc/apache2/conf.d/phpmyadmin.conf
cat: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
root@doug-laptop:/home/doug# 


/etc/phpmyadmin/ contains 

(just so you don't think I didn't install phpmyadmin lol)

> root@doug-laptop:/home/doug# cat /etc/apache2/conf.d/phpmyadmin.conf
cat: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
root@doug-laptop:/home/doug# 

/etc/apache2/ contains

[quote]root@doug-laptop:/home/doug# ls /etc/apache2/
apache2.conf  envvars     mods-available  ports.conf       sites-enabled
conf.d        httpd.conf  mods-enabled    sites-available


/etc/apache2/conf.d only contains a single file charset

---

### Post by wdaniels on 2008-06-24
> **DougAlder said:**
> to install PhpMyAdmin which in turn installed Apache 2 and MySQL 5.

I just re-read your post and noticed this. Perhaps it didn't get configured right because apache2 was not already installed at the time. Try re-configuring phpmyadmin package now that apache2 is already installed and see if it configures the alias properly:

```
sudo dpkg-reconfigure phpmyadmin
```

---

### Post by DougAlder on 2008-06-24
> **wdaniels said:**
> I just re-read your post and noticed this. Perhaps it didn't get configured right because apache2 was not already installed at the time. Try re-configuring phpmyadmin package now that apache2 is already installed and see if it configures the alias properly:

```
sudo dpkg-reconfigure phpmyadmin
```

OK just did that - it came up showing Apache2 I hit OK then tried localhost/phpmyadmin again and still got the 404

---

### Post by wdaniels on 2008-06-24
Hmm, was there a star next to apache2, like this:

```
[*] apache2
```

Does the phpmyadmin.conf file exist now or not?

If not, I would try completely removing phpmyadmin and install it again:

```
sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin

```

If that still doesn't work, I guess we could configure apache manually...

---

### Post by DougAlder on 2008-06-24
> **wdaniels said:**
> Hmm, was there a star next to apache2, like this:

```
[*] apache2
```

Does the phpmyadmin.conf file exist now or not?

If not, I would try completely removing phpmyadmin and install it again:

```
sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin

```

If that still doesn't work, I guess we could configure apache manually...

No I'm still getting a file not found

> root@doug-laptop:/home/doug# cat /etc/apache2/conf.d/phpmyadmin.conf
cat: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory


I'll try your suggestion above and let you know

---

### Post by DougAlder on 2008-06-24
OK I uninstalled then reinstalled phpmyadmin got all the same responses as before.

[QUOTE]root@doug-laptop:/home/doug# cat /etc/apache2/conf.d/phpmyadmin.conf
cat: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory[/QUOTE

when the phpmyadmin configration tool ran it had preselected Apache 2 - [] box highlighted in red but there was no * in it. I couldn't see any way to input anything other than hitting enter for OK which is what I did

---

### Post by wdaniels on 2008-06-24
> **DougAlder said:**
> when the phpmyadmin configration tool ran it had preselected Apache 2 - [] box highlighted in red but there was no * in it. I couldn't see any way to input anything other than hitting enter for OK which is what I did

Ah, this is your problem then! Use space to toggle the asterisk mark. It is a text-based equivalent to a check box, no star = not checked. The command to reconfigure again is:

```
sudo dpkg-reconfigure phpmyadmin
```

---

### Post by DougAlder on 2008-06-24
> **wdaniels said:**
> Ah, this is your problem then! Use space to toggle the asterisk mark. It is a text-based equivalent to a check box, no star = not checked. The command to reconfigure again is:

```
sudo dpkg-reconfigure phpmyadmin
```

BINGO! Damn you'd think I would have remembered that from my old DOS days - sigh oldsheimers is getting to me ;)

A very big thank you Mr. Daniels. It's working now

---


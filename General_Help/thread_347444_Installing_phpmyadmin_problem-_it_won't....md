---
title: "Installing phpmyadmin problem- it won't..."
date: 2007-01-27
forum: General Help
---

### Post by tiger.woods on 2007-01-27
Did an apt-get install phpmyadmin and it has been installed on the system but all I get is a blank screen when trying to login??? What gives?? 

Did a LAMP install on this box so all the supporting pieces should be there.

What have I missed?

T.I.A

---

### Post by Koybe on 2007-01-27
Did you try restarting apache?
Is your browser javascript enabled?
What's happening if you just get to [http://localhost/](http://localhost/) ?

---

### Post by tiger.woods on 2007-01-27
> Did you try restarting apache?

Yes.


> Is your browser javascript enabled?

Yes.


> What's happening if you just get to [http://localhost/](http://localhost/) ?

I get a directory containing 'Apache2-default' and 'phpmyadmin' folders. If I go into the phpmyadmin folder I get a blank white screen.

---

### Post by az on 2007-01-27
Would you list all the LAMP stack packages you have installed?

---

### Post by tiger.woods on 2007-01-27
I'm a bit new so can you elaborate just a bit? If you mean which of the LAMP applications I installed, I've installed them all.

Thanks,

---

### Post by Koybe on 2007-01-27
you can use 
```
dpkg -l apache*
dpkg -l libapache*
``` to show what's installed related to apache.

You also need the php4-mysql (or php5-mysql) package.

Make sure php is started :
```
sudo a2enmod php4 (or 5)
```

you can try php by creating an index.php containing 
```
<? phpinfo(); ?>
```

I hope this maybe can help.

---

### Post by tiger.woods on 2007-01-27
I believe all the pieces are installed, PHP5, mysql and phpmyadmin but I don't think they are talking?? 

If I installed phpmyadmin from apt is there any setup needed or should it just work?


> mythtv@myth:~$ dpkg -l apache*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
un  apache-common       <none>              (no description available)
un  apache-utils        <none>              (no description available)
ii  apache2             2.0.55-4ubuntu4     next generation, scalable, extendable web server
ii  apache2-common      2.0.55-4ubuntu4     next generation, scalable, extendable web server
un  apache2-doc         <none>              (no description available)
un  apache2-modules     <none>              (no description available)
un  apache2-mpm-perchil <none>              (no description available)
ii  apache2-mpm-prefork 2.0.55-4ubuntu4     traditional model for Apache2
un  apache2-mpm-threadp <none>              (no description available)
un  apache2-mpm-worker  <none>              (no description available)
ii  apache2-utils       2.0.55-4ubuntu4     utility programs for webservers

mythtv@myth:~$ dpkg -l libapache*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
un  libapache-mod-auth- <none>              (no description available)
un  libapache-mod-perl  <none>              (no description available)
un  libapache2-mod-auth <none>              (no description available)
un  libapache2-mod-php4 <none>              (no description available)
ii  libapache2-mod-php5 5.1.6-1ubuntu2.1    server-side, HTML-embedded scripting language (apache

mythtv@myth:~$ sudo a2enmod php5
This module is already enabled!

---

### Post by Koybe on 2007-01-27
If they aren't talking maybe you're missing php5-mysql package, do you?

---

### Post by tiger.woods on 2007-01-27
nope, got it.

---

### Post by Koybe on 2007-01-27
Edit : misunderstood.

Your problem look strange. And what if you try a phpinfo page ?


Could you put this output : 

```
ls -l /etc/apache2/conf.d/
ls -l /etc/apache2/sites-enabled/
```

---

### Post by tiger.woods on 2007-01-27
Is there a "How to" for install phpmyadmin on ubuntu??? Should it be as as simple as apt-get install phpmyadmin??


mythtv@myth:/home$ ls -l /etc/apache2/conf.d
total 4
-rw-r--r-- 1 root root 24 2007-01-24 17:33 charset
mythtv@myth:/home$ ls -l /etc/apache2/sites-enabled
total 0
lrwxrwxrwx 1 root root 36 2007-01-24 17:33 000-default -> /etc/apache2/sites-available/default

---

### Post by tiger.woods on 2007-01-27
Anyone?

---

### Post by Koybe on 2007-01-28
Sorry, it was time to go for me.

I do not have it install in front of me, but i can see this in the package :
usr/share/ucf/phpmyadmin/etc/phpmyadmin/apache.conf    

So maybe you can try :

```
cp /usr/share/ucf/phpmyadmin/etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phphmyadmin.conf
```Restart apache et retry accessing. Maybe you can post this file to as I don't have any apache installed right now.

---

### Post by tiger.woods on 2007-01-28
Still the same, it finds the page, the browser says "Done" but it's just plain white...

---

### Post by tiger.woods on 2007-01-28
Gave up on it and installed Wine then SQLYog... thanks for the help though.

---

### Post by Koybe on 2007-01-28
Pity... anyway you can also download phpmyadmin on the phpmyadmin site, decompress it to your www folder... and it's already nearly working. ;)

---

### Post by tiger.woods on 2007-01-28
Well if I hadn't spent most of the day yesterday banging on it with little progress I may have had the inclination to keep on keeping on...

Wind and SQLYo, installed in 2 minutes... kind of a no brainer as far as time/value.

I certainly appreciated your suggestions though.

TW,

---


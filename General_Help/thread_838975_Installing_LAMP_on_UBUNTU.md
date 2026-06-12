---
title: "Installing LAMP on UBUNTU"
date: 2008-06-24
forum: General Help
---

### Post by ivssatish on 2008-06-24
I have recently switched from Windows to Ubuntu Desktop edition 8.04 and must have it is quite overwhelming. However, I would like to set up LAMP on my desktop edition and want to learn how to host a website and build my own pages (hope I put it in right words). Is it feasible? If not, do I need to install server edition on my laptop and does it have all the GUI interfaces as the desktop edition has?

I need direction from you expert guys and can't wait to get the answer as I am really excited by the features of Linux. I am so dying to learn all(may be not all but a good amount) about Linux and LAMP ... 

Please help guys...

Thanks,
Satish

---

### Post by VMC on 2008-06-24
> **ivssatish said:**
> I have recently switched from Windows to Ubuntu Desktop edition 8.04 and must have it is quite overwhelming. However, I would like to set up LAMP on my desktop edition and want to learn how to host a website and build my own pages (hope I put it in right words). Is it feasible? If not, do I need to install server edition on my laptop and does it have all the GUI interfaces as the desktop edition has?

I need direction from you expert guys and can't wait to get the answer as I am really excited by the features of Linux. I am so dying to learn all(may be not all but a good amount) about Linux and LAMP ... 

Please help guys...

Thanks,
Satish

I don't know anything about LAMP, but here is a link with all the instructions to set it up on ubuntu:
[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

---

### Post by chiskop on 2008-06-24
Good help available [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").
If you're wanting to learn it's really not necessary to install the server-edition, just add a server onto what you're currently using.
Use:
```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

```

That will install a server on your laptop - you'll still have your desktop etc.

---

### Post by mcduck on 2008-06-24
No need for Server edition, all server software runs on normal desktop edition,a nd all desktop software can be installe don the server edition. Actually thy are the same, only with different stuff included by default.

Anyway, the easiest way to get LAMP installed is to use Synaptic. In the menu find the "Mark Packages by Task", open that and enable "LAMP server".

I recommend getting the phpmyadmin package as well, makes managing your SQL databases much easier..

---

### Post by ivssatish on 2008-06-24
Now, I am trying to test the successful of PHP by doing the following:

nano /var/www/test.php

# test.php
<?php phpinfo(); ?>

and then pointing my browser to [http://localhost.com/test.php](http://localhost.com/test.php) 

A dialogue box opens prompting to save or open the file test.php instead of displaying the PHP info in the browser itself. 

I have restarted my machine but no luck.Please see the attachment for a screenshot

P.S I am also noticing similar behaviour on [http://localhost.com/phpmyadmin](http://localhost.com/phpmyadmin) after trying to log in with root as the user and a password and press enter. The only difference is that the file name index.php.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5251050](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5251050)
Please help folks.:confused:

---

### Post by manfer on 2008-06-25
Had you solved it?

I think it is only that you need to restart apache.

prompt:~$ **sudo /usr/sbin/apache2ctl restart**

If you just has restarted your computer in the last hours maybe that has solved the issue too.

---

### Post by ivssatish on 2008-06-25
Thanks for your advise mcduck, chispok and VMC!!!. Now I have a new stumbling block.... can you please help me with it? I will really appreciate that.... Satish

---

### Post by ivssatish on 2008-06-25
I have done both but no luck .....I am completely lost!!!!

---

### Post by indytim on 2008-06-25
A little late, but for future reference on easy installation:

```

$ sudo tasksel

```

IndyTim

---

### Post by keiffee30 on 2008-06-25
i have had the same problem with Firefox asking to download files when it should be opening them. 

This is due to Apache 2 is not talking to PHP 5. The work around on this is to reinstall Apache then PHP then MySQL. I will find the link for you that i used to do a manual install. I found this to be the best way to install LAMP. 

Just one more point. The best way i can put this is ,......

Linux is the OS. Then the different GUI like Gnome , KDE , X11 can be put ontop of the OS. so it dosen't matter if the CD / DVD is called server or desktop its the same OS but with a diffrent desktop too it.

I know im going to get shot for saying that but i too have come from a Windoze and im loving ubuntu from 6.10 - 8.04.

This is the link you will need to sort out this problem, and it is in plain and simple to use / read
[https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/)

---

### Post by MacAnthony on 2008-06-25
Try making just a test html page (no php) to see. Looks like either apache isn't configured to handle php_mod or either apache or php is sending the wrong mime-type to the browser.

---

### Post by Ryklou on 2008-06-25
I think you ment lampp :KS
Source: [http://www.apachefriends.org/en/xampp-linux.html#374]("http://www.apachefriends.org/en/xampp-linux.html#374")

You can also install XAMPP, that give's you the ability of hosting your ow web file's.

Instilation file: 58MB
Click to DL-->[xampp-linux-1.6.6.tar.gz]("http://www.apachefriends.org/download.php?xampp-linux-1.6.6.tar.gz")

Apache 2.2.8, MySQL 5.0.51a, PHP 5.2.5 & 4.4.8 & PEAR + SQLite 2.8.17/3.3.17 + multibyte (mbstring) support, Perl 5.10.0, ProFTPD 1.3.1, phpMyAdmin 2.11.4, OpenSSL 0.9.8e, GD 2.0.1, Freetype2 2.1.7, libjpeg 6b, libpng 1.2.12, gdbm 1.8.0, zlib 1.2.3, expat 1.2, Sablotron 1.0, libxml 2.6.31, Ming 0.3, Webalizer 2.01, pdf class 009e, ncurses 5.8, mod_perl 2.0.2, FreeTDS 0.63, gettext 0.11.5, IMAP C-Client 2004e, OpenLDAP (client) 2.3.11, mcrypt 2.5.7, mhash 0.8.18, eAccelerator 0.9.5.2, cURL 7.17.1, libxslt 1.1.8, phpSQLiteAdmin 0.2, libapreq 2.08, FPDF 1.53, XAMPP Control Panel 0.6 

```
[COLOR="DarkRed"]MD5 checsum: e534fbfd0a9d1553a4abecb73784828f[/COLOR]
```

After downloading simply type in the following commands:

   1. Go to a Linux shell and login as the system administrator root:

      ```
su
```

   2. Extract the downloaded archive file to /opt:

      ```
tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
```

      Warning: Please use only this command to install XAMPP. DON'T use any Microsoft Windows tools to extract the archive, it won't work.

      Warning 2: already installed XAMPP versions get overwritten by this command.

That's all. XAMPP is now installed below the /opt/lampp directory.
* Step 3: Start
To start XAMPP simply call this command:

```
/opt/lampp/lampp start
```

You should now see something like this on your screen:

> Starting XAMPP 1.6.6...
LAMPP: Starting Apache...
LAMPP: Starting MySQL...
LAMPP started.

Ready. Apache and MySQL are running.

If you get any error messages please take a look at the Linux FAQ.
* Step 4: Test
OK, that was easy but how can you check that everything really works? Just type in the following URL at your favorite web browser:
EDIT
Were Your Web File's Should and are Located:

[COLOR="Sienna"]/opt/lammp/htdocs[/COLOR]
END EDIT

[http://localhost](http://localhost)

Now you should see the start page of XAMPP containing some links to check the status of the installed software and some small programming examples.

[IMG]http://www.apachefriends.org/images/380.jpg[/IMG]

---

### Post by manfer on 2008-06-25
Can you start the process from scratch or you have something in your servers (web server, mysql..)?

If you can do it from scratch do the following;

---------------------

First, uninstall and purge:

prompt:~$ **sudo apt-get purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql**

---------------------

Second, reinstall of LAMP:

prompt:~$ **sudo tasksel install lamp-server**

---------------------

Third, test apache in firefox, **[http://localhost](http://localhost)**. You should see "It works"

---------------------

Fourth, a php test:

Create **test.php** in **/var/www** with the content you just know:

[B]# test.php
<?php phpinfo(); ?>[/B]

restart apache (probably not need too but restart, or try it first if you want):

prompt:~$ **sudo /etc/init.d/apache2 restart**

Test now in firefox, **[http://localhost/test.php](http://localhost/test.php)**

---------------------

Fifth, install phpmyadmin.

prompt:~$ **sudo apt-get install phpmyadmin**

It will ask you which version of apache you have. Press space to select apache2, press tab to move focus to button accept, and press enter. That installs phpmyadmin, reconfigures apache2, and restarts it. You will see it in terminal.

Now test the phpmyadmin **[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)**, you would see phpmyadmin login.

---------------------

*If for any reason localhost doesn't work (it worked for you before so I think it is going to work), try **[http://127.0.0.1](http://127.0.0.1)** instead in all cases.*

---

### Post by Ryklou on 2008-06-25
ok, you can install myphpadmin, sql, php, cgi, pl, everything with XAMPP, i use it everyday.

Just wanted to tell you that, keeps you from having to type, alot in the terminal :)

(my2cents)

---

### Post by manfer on 2008-06-26
Only a note.

I think many of the features of Ming can be illegal in many countries where personal privacy is protected by law. It is included in XAMPP.

---

### Post by ivssatish on 2008-06-27
Thanks a lot Manfer!!! It worked!!! I started all over as you suggested and I am happy now... thanks again

---

### Post by sidrit on 2008-08-10
Voilà the lamp server on hardy in a few steps.

[http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/]("http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/")

;) hope it helps.

---

### Post by Ryadt on 2008-08-10
Why are you guys installing LAMP the hard way?
Just go in Synaptic > Edit > Mark Packages by task. Select LAMP server and click OK.

---

### Post by colinmccubbin on 2010-01-26
> **Ryadt said:**
> Why are you guys installing LAMP the hard way?
Just go in Synaptic > Edit > Mark Packages by task. Select LAMP server and click OK.

Hey, thanks, just tried that and it worked a treat!:P

Got the "It works!" page from locahost so apache is running, but it would be great if that page (presumably index.htm or index.html) told me where the ht_docs folder or whatever it is called  within which pages reside actually is, rather than me now having to go look for an index.htm(l)...

Edit: Found it, it is in: *filesystem/var/www/*

I created a file containing <?php phpinfo();?> saved it there as phpinfo.php.  Ran [http://localhost/phpinfo.php](http://localhost/phpinfo.php)  only to get a message from firefox "What should Firefox do with this file"  So PHP is not running. Now I'm stuck again!

So, now I need to change that default location to a ntfs partition on my dual boot box since most of my pages are composed in WinXP/Dreamweaver and sadly Ext2IFS which used to work to allow windows to write to EXT2 and 3 systems no longer works with the EXT4 that Ubuntu 9.10 now uses..:-(:-(  Can anyone help with that, please?

I'm desperately trying to dump Windows, but....

---

### Post by colinmccubbin on 2010-01-26
Rebooted... [http://localhost/phpinfo.php](http://localhost/phpinfo.php) now works.. 

But I'm still stuck on moving the localhost root from from var/www/ to my shared ntfs partition. 

In the ntfs partition I have created a folder called htdocs, from which I'd like apache and localhost to serve pages. I then right clicked it, selected "Make link", and then copied the resulting "Link to htdocs" and dropped it into var/www/


I then placed phpinfo.php in htdocs, and issued the command [http://localhost/phpinfo.php](http://localhost/phpinfo.php) expecting it to be served from htdocs/ but just get a 404 file not found. 

I should probably post this in the beginners section since that is what I am, but rather than double post would really like a simple explanation to get me going.

Thanks!

---

### Post by Wolfpup on 2010-01-29
> **Ryadt said:**
> Why are you guys installing LAMP the hard way?
Just go in Synaptic > Edit > Mark Packages by task. Select LAMP server and click OK.


i did the as well but i can not get the xamp page and i have forgoten hoe to male a file with php extension.

---


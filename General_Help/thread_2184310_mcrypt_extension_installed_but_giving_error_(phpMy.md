---
title: "mcrypt extension installed but giving error (phpMyAdmin)"
date: 2013-10-28
forum: General Help
---

### Post by bddenhartog on 2013-10-28
Hey all. I'm fairly new to server setup through the command line, but have had a bit of experience on CentOS and used some tutorials to get everything set up on my Ubuntu 13.10 desktop installation.

Steps taken:

```
$ sudo apt-get install tasksel
$ sudo tasksel install lamp-server
$ sudo apt-get install phpmyadmin
```

At this point, the phpmyadmin package states that it installs php5-mcrypt. However, after browsing to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and logging in, I am shown the following alert at the bottom of the page:

> The [*mcrypt*]("http://localhost/phpmyadmin/url.php?url=http%3A%2F%2Fphp.net%2Fmanual%2Fen%2Fbook.mcrypt.php&token=a69ad7e7c5a2f7a207dd3b27b2d30425") extension is missing. Please check your PHP configuration.




Doing some searching showed that other people have run into this issue. Great -- solutions!

- I've checked the mcrypt.ini file, it has the correct "extension=mcrypt.so" line.
- I've removed the phpmyadmin package, reinstalled it, and reinstalled php5-mcrypt
- Yes, I've restarted my apache2 service after every package change

Using phpinfo(); displays the mcrypt module authors, but it is not listed anywhere else in the output.

I am **still** getting this error. Anybody have a fix for me?

---

### Post by SeijiSensei on 2013-10-28
Install the **php5-mycrypt** package from the Ubuntu repositories then restart the web server.  Debian and Ubuntu package many PHP modules separately rather than integrating them all like RedHat/CentOS does.

---

### Post by bddenhartog on 2013-10-28
Sorry if I wasn't clear -- I've already tried installing **php5-mcrypt** using *sudo apt-get install php5-mcrypt*. I am still shown the error.

---

### Post by SeijiSensei on 2013-10-29
Looks like the php5-mcrypt module is not packaged correctly, probably because of the switch from Apache 2.2 to 2.4 in the 13.10 release.  It looks to have caused some other problems as well.

Here are the steps I followed to activate the module:

1)  The mcrypt.ini file in /etc/php5/conf.d needs to be copied or symlinked to /etc/php5/mods-available:

```
cd /etc/php5/mods-available
sudo ln -s ../conf.d/mcrypt.so

```

I used a symlink in case something might break if the module is moved.

2)  Activate the module with "sudo php5enmod mcrypt".

3)  Restart Apache.

I recommend you create a file called /var/www/info.php or something similar with just this contents:

```
<?php phpinfo() ?>
```

Now if you navigate to [http://127.0.0.1/info.php](http://127.0.0.1/info.php) you will see a complete inventory of your installation and all the various global variables and arrays available to you.  There should be an "mcrypt" stanza on the page if the module loads correctly.

I'll take a look and see if there's a bug report for this.  If not, I'll submit one unless you want to.

**Update:** It has [already been reported](https://bugs.launchpad.net/ubuntu/+source/php-mcrypt/+bug/1240590).

I will say that if you are intending to use this server in production, you should be running the 12.04LTS release of the Server Edition, not the 13.10 release. The LTS releases are designed to remain stable; 12.04 will be supported through 2017.  13.10 will reach end-of-life next year.   The LTS releases are more in the style of RedHat/CentOS with older, more stable software designed for long, uninterrupted use.  Ubuntu is much more volatile, especially any release which does not have long-term support like 12.04.

---

### Post by bddenhartog on 2013-10-29
Thank you for the full breakdown. I'm new to Ubuntu, your post was incredibly helpful.

I am not using this for production -- just for local development. Thanks though - I'm sure that'll save someone who isn't aware!

---

### Post by j-prause on 2013-12-04
> **SeijiSensei said:**
> 
```

sudo ln -s ../conf.d/mcrypt.so

```

As to me, 'mcrypt.so' should read 'mcrypt.ini'.

Anyway, I also thank you for your hint, it solved the issue for me (using mcrypt.ini in the command above).

---


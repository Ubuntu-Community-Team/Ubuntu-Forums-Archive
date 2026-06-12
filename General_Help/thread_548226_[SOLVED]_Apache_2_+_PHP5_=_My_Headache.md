---
title: "[SOLVED] Apache 2 + PHP5 = My Headache"
date: 2007-09-11
forum: General Help
---

### Post by rivalarrival on 2007-09-11
This is probably a simple fix, but I can't figure it out... Running 7.04...

Summary:
I think the apache php5 module is broken/misconfigured/posessed by demons, but I don't know enough to verify that... It seems like enabling the php5 module will only allow files with .php extensions to be served, and it does not parse these as php scripts. I get a weird error when I restart apache with the php5 module enabled - httpd (no pid file) not running.

Detail:
/var/www contains the apache2-default,   test.php (not a properly formatted php file) testphp.php (<?php phpinfo(); ?>) and test.html

```
sudo apt-get install apache2
```
apache2 installs, and serves correctly for this stage (browser asks if you want to save the php file)

 Now I go for php5

```
sudo apt-get install php5 libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 force-reload

```
returns appropriate responses, but browsing to localhost, localhost/apache2-default, or localhost/test.html says "unable to connect"

browsing to [http://localhost/testphp.php](http://localhost/testphp.php) or test.php prompts to download the php script. When I restart apache now, I get:

```
  * Forcing reload of web server (apache2)...
httpd (no pid file) not running
                                                                         [ OK ]

```

Disabling the PHP5 module and restarting:
```
sudo a2dismod php5
sudo /etc/init.d/apache2 force-reload

```
gives the same "httpd (no pid file) not running" error as above, but apache starts serving all files again. I have never been able to get a php file to parse at all.

---

### Post by PreviousN on 2007-09-11
If you want to start from scratch, try "apt-get --purge remove apache2 php5 libapache2-mod-php5" 

There could be some config file that doesn't get uninstalled when you're using the regular apt-get remove. Thats my guess, it could be wrong. Don't kill me if it messes up your system.

---

### Post by rivalarrival on 2007-09-11
Same behavior after reinstall - I assume the --purge option is similar to Synaptic's complete removal option? 

with php5 module enabled, server permits only php files to be downloaded - won't load html or flat files, won't parse the php files.

I'm at a loss. I'm reading dozens of testimonials about how it "just works" and I'm starting to think that I don't pay enough attention to my server's needs...

---

### Post by rivalarrival on 2007-09-11
[SOLVED]

One of those "Sleep on it, and it will work tomorrow" problems...  I run into those a lot...

Basically, because I don't really know what I'm doing, I just emulate the appearance, I wasn't completely removing the configuration files when I did as PreviousN suggested.

After I completed his instructions, I did a sudo apt-get --purge autoremove to take care of the other packages and the error messages said that /etc/apache2 and /etc/php5 were not empty so not removed...

gksu nautilus and deleted both of them, reinstalled via synaptic > edit > mark packages by task and apparently, the linux gods and daemons were smiling on me because it just fricken worked.

Wish I knew how I broke it in the first place, but I'll chalk it up to the stupid things I did while starting to learn.

---


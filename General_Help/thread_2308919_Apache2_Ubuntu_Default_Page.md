---
title: "Apache2 Ubuntu Default Page"
date: 2016-01-06
forum: General Help
---

### Post by Mel_Blakey on 2016-01-06
I have Ubuntu 14.04 LTS on my lappy and I have just removed 'xampp'. To ensure that I didn't have a 2nd instance of xampp installed I typed 'localhost' into my browser and it came with "Apache2 Ubuntu Default Page" 
[IMG]http://buttyandsweet.co.uk/images/s-shot_0601-2016_ubuntu.jpeg[/IMG]

Is this a normal part of Ubuntu or do I have another server running in the background.

I'm pretty new to linux if you think that its a stupid question!

---

### Post by SeijiSensei on 2016-01-06
You have a copy of Apache running.  Try "ps ax | grep apache".  You should see lines like this:
```
19741 ?        S      0:00 /usr/sbin/apache2 -k start
```

---

### Post by Mel_Blakey on 2016-01-06
I decided to 'try' and install Lamp instead as I read that it would be an easier and more secure alternative and in the process I have answered my own question as it seems that I have by proxy all of the components required to make up Lamp. I have hit a brick wall with lamp as well. So, I've had enough. I've spent all of today and the best part of yesterday trying to get Joomla to run on my local machine. Unfortunately, it is way above me and I admit defeat.

What is the best, quickest & simplest way to get all of this unnecessary stuff of my machine and clean up?

I really would appreciate some advice.

Thanks!

---

### Post by Mel_Blakey on 2016-01-06
Sorry, I cross posted. Thanks for replying.

ps ax | grep apache
```

 1348 ?        Ss     0:00 /usr/sbin/apache2 -k start
 1446 ?        S      0:00 /usr/sbin/apache2 -k start
 1447 ?        S      0:00 /usr/sbin/apache2 -k start
 1448 ?        S      0:00 /usr/sbin/apache2 -k start
 1449 ?        S      0:00 /usr/sbin/apache2 -k start
 1450 ?        S      0:00 /usr/sbin/apache2 -k start
 2728 ?        S      0:00 /usr/sbin/apache2 -k start
28240 pts/8    S+     0:00 grep --color=auto apache

```

---

### Post by SeijiSensei on 2016-01-06
> **Mel_Blakey said:**
> What is the best, quickest & simplest way to get all of this unnecessary stuff of my machine and clean up?
Honestly, I'd reinstall Ubuntu.  At a minimum you'll need to remove apache2, php and its associated packages, and mysql.

However I'd recommend giving WordPress a try instead of Joomla or Drupal.  For that you need to install the lamp-server meta package like this:
```
sudo apt-get install lamp-server^
```
For more details, read this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You can install WordPress from the Ubuntu repositories, though I usually just download the zip file from wordpress.org and unpack it where I want the website to be located.

In the future, you might consider installing VirtualBox on your machine then creating a virtual machine into which you can install another copy of Ubuntu like Ubuntu Server.  You can muck around in the VM without affecting the actual machine that is hosting the virtual one.  I recommend installing VirtualBox by following the instructions here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by Mel_Blakey on 2016-01-06
Hi and thanks for the advice. I think that a fresh Ubuntu install would be easiest.

I have played about with Wordpress, but I cut my teeth on Joomla, starting with 1.5 so I'm more comfortable with it. Does it perform OK on Lamp?

---

### Post by SeijiSensei on 2016-01-06
They both use the same infrastructure as far as I know - Apache, PHP and MySQL.  I prefer PostgreSQL myself, but WP doesn't support that natively so I have both MySQL and PostgreSQL on my servers running WordPress.

---

### Post by Mel_Blakey on 2016-01-07
Thanks for your input & advice!

---


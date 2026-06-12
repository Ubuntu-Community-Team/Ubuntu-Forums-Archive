---
title: "Quantal (12.10) PHP 5.4 downgrade to 5.3"
date: 2012-10-21
forum: General Help
---

### Post by foxy202 on 2012-10-21
Hi All 
  as most of you i have problem with PHP 5.4 after upgrade my Ubuntu to  Quantal (12.10).

Here is my solution how i downgrade php 5.4 to 5.3... it help me a lot

just to mention it is based on Original script for 5.3 by Ruben Barkow

---

### Post by 2union on 2012-10-22
Great work, thank you!:guitar:

---

### Post by pedectrian on 2012-10-22
Thanx! You really helped me! Tried to restore 5.3 since friday! :)

---

### Post by ssayen on 2012-10-22
Many thanks Foxy you saved me a lot of time ;)

---

### Post by VanSanblch on 2012-10-22
Extremely useful script.

Thank you very much.

---

### Post by pqwoerituytrueiwoq on 2012-10-22
What is wrong with 5.4?

---

### Post by TheOnlyEnglishRose on 2012-10-22
I get nothing but blank pages. Granted, that's because I'm in the process of rewriting a PHP 4 application to work with PHP 5.3 but enough was changed between PHP 5.3 and 5.4 to break some applications such as mine.

If you're using things that are expertly maintained like Wordpress, Joomla, Drupal, etc. PHP 5.4 should be perfectly fine.

---

### Post by pqwoerituytrueiwoq on 2012-10-22
sounds like a error in your php
see line 480 of /etc/php5/apache2/php.ini

---

### Post by wasif0122 on 2012-10-24
[foxy202]("http://ubuntuforums.org/member.php?u=828382") Thanks! been looking for a solution

---

### Post by jxn on 2012-10-24
HatTip to you, foxy202.  You have saved me some time.  Unfortunately, I am already mourning the loss of php5 features.

---

### Post by Telefo on 2012-10-29
Thanks! Very useful! But if I want to reinstall the last version? Can I remove all the files in /etc/apt/preferences.d/php5_3, remove the sourcelist entry and then update? 
 
 
 is it enough?

---

### Post by sebaskut on 2012-11-06
Thank you so much !

---

### Post by Stickee on 2012-11-06
Thanks OP!

---

### Post by abhi555 on 2012-11-09
Thanks. Great job

---

### Post by joseangelsosa on 2012-11-10
Thank you so much!

---

### Post by ramsondon on 2012-11-15
PHP downgrade works like expected, but phpunit is broken

phpunit  -v
PHP Fatal error:  Call to undefined method PHP_CodeCoverage_Filter::getInstance() in /usr/bin/phpunit on line 39


Resolved by:
sudo pear channel-update pear.phpunit.de
sudo pear install phpunit/PHP_CodeCoverage
sudo pear install --force --alldeps phpunit/PHPUnit

just for the record!
greez

---

### Post by embeehere on 2012-11-20
Clicking my heels and saluting you. This worked like a charm and saved the day. An upgrade to 12.10 automatically upgraded php, rendering one of our third party  software useless. This downgrade script helped us a lot.

---

### Post by ansaro on 2012-11-21
> **pqwoerituytrueiwoq said:**
> What is wrong with 5.4?

Theres a lot of software using, for example, allow_call_time_pass_reference directive, and it doesn't work on php 5.4 ...

You won a beer fox202 :mrgreen:

---

### Post by vazoom on 2012-11-25
I had to do the downgrade which seemed to work ok.  The problem now however is that I need to install the IMAP module for PHP as reference by my posting here: [http://ubuntuforums.org/showthread.php?t=2088213](http://ubuntuforums.org/showthread.php?t=2088213)
 
I cannot figure out what I must do to get this module installed.  Thanks

---

### Post by buric on 2012-11-27
Thank you so much...
I couldn't install Magento on my PHP 5.4.
Now it works perfectly!
=D>

---

### Post by wesleyvioto on 2012-11-28
Thank's ... excelent script ... :guitar:

---

### Post by duhd on 2013-01-07
Thanks a million ! You are a lifesaver !!!!!

---

### Post by faspina on 2013-01-13
Thanks!  Just upgraded to Ubuntu 12.10, my phprecipedb stopped working. Figured out that it was PHP, did a google search and BAM!  Running the script now, we will see what happens. 

Also just joined the forum. I will be investigating a lot here.

---

### Post by matthemattical on 2013-01-23
Ah, thank you! That's extremely helpful.

Panels for Drupal 6 doesn't work well with PHP 5.4, and this has solved my problem.

---

### Post by newearthman on 2013-01-30
Thank you very much. Worked well. PHP 5.3 is still recommended for Drupal 6 and 7.

Does it also prevent PHP from being upgraded automatically by the update manager?

---

### Post by karnival8 on 2013-02-02
i did the downgrade, turns out it made my problems worse. 

now i can't php back up again. huge problem.

```
vm@vmserver:~$ sudo apt-get install php5 -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php5 : Depends: libapache2-mod-php5 (>= 5.4.6-1ubuntu1.1) but 5.3.10-1ubuntu3 is to be installed or
                 libapache2-mod-php5filter (>= 5.4.6-1ubuntu1.1) but it is not going to be installed or
                 php5-cgi (>= 5.4.6-1ubuntu1.1) but it is not going to be installed or
                 php5-fpm (>= 5.4.6-1ubuntu1.1) but it is not going to be installed
        Depends: php5-common (>= 5.4.6-1ubuntu1.1) but 5.3.10-1ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.
vm@vmserver:~$ 

```

---

### Post by muratsac on 2013-02-07
How to install PHP 5.3.20?

---

### Post by foxy202 on 2013-02-19
Thank you all.

Some packages give Depends problem: 

apt-get install php5-curl
..............
..............
The following packages have unmet dependencies:
 php5-curl : Depends: phpapi-20100525
             Depends: php5-common (= 5.4.6-1ubuntu1.1) but 5.3.10-1ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.


 Just to note first of all to check is it they exist in /etc/apt/preferences.d/php5_3 file ...

in my case i just add follow 

Package: php5-curl
Pin: release a=precise
Pin-Priority: 991

Then: 
   #apt-get update
   #apt-get install php5-curl

and work fine. It could help and for other PHP 5.3 packages

---

### Post by tpartridge on 2013-03-05
Thank you for this script! It saved me a ton of time.

After the script finished, apache2 failed to restart, showing me "apache2ctl: command not found." I was able to resolve this by reinstalling apache2:

*$ sudo apt-get install apache2*

---

### Post by virendrachandak on 2013-03-15
Thank you for the script, it worked. However, When I tried to install other packages like GD, I got the following error:


```

The following packages have unmet dependencies:
 php5-gd : Depends: phpapi-20100525
           Depends: php5-common (= 5.4.6-1ubuntu1.2) but 5.3.10-1ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Below post from "foxy202" helped me to fix the issue to install php5-gd.

> **foxy202 said:**
> Thank you all.

Some packages give Depends problem: 

apt-get install php5-curl
..............
..............
The following packages have unmet dependencies:
 php5-curl : Depends: phpapi-20100525
             Depends: php5-common (= 5.4.6-1ubuntu1.1) but 5.3.10-1ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.


 Just to note first of all to check is it they exist in /etc/apt/preferences.d/php5_3 file ...

in my case i just add follow 

Package: php5-curl
Pin: release a=precise
Pin-Priority: 991

Then: 
   #apt-get update
   #apt-get install php5-curl

and work fine. It could help and for other PHP 5.3 packages

---

### Post by virendrachandak on 2013-03-15
> **muratsac said:**
> How to install PHP 5.3.20?

I would also like to install the latest version of PHP 5.3.x (5.3.22). Does anyone knows how we can do that?

---

### Post by scndsky on 2013-05-06
Excellent script. Thanks!

---

### Post by XaaL on 2013-05-29
Do you think this might work under debian wheezy? I don't want to screw everything up i did so far... but apprearently i really need this.

---

### Post by cottonec on 2013-06-12
Works most than perfectly

---

### Post by cary2 on 2013-10-17
echo "My Thanks"

---

### Post by kwemart on 2013-12-21
Hi to all!
I've used this code to downgrate my php version, but this cause my phpmyadmin to become unaccessible and and right now mysql does not work any more
what can I do to repair this?
I've tried to reinstall apache and phpmyadmin but the système has freeze to php 5.3.
Need help.
Thanks!

---


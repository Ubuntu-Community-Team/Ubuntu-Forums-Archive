---
title: "Problem on PHP version"
date: 2023-02-14
forum: General Help
---

### Post by satimis on 2023-02-14
Hi all

I have cloned websites installed on VMs running on Ubuntu 20.04.  I expect to import them to VirtualBox running on Ubuntu22.04.

**[COLOR="#FF0000"]Now the problem is PHP version;[/COLOR]**
Ubuntu 20.04 - php-7.4
Ubuntu 22.04 - php-8.1

I can downgrade Ubuntu 22.04 php-8.1 to php-7.4 but this is not a good solution because php-7.4 will be out soon.

Is there anyway to upgrade the php version on all websites to php-81?  Please advise.  Thanks in advance.

Regards

---

### Post by SeijiSensei on 2023-02-14
Wasn't hard to find the answer: [https://linuxize.com/post/how-to-install-php-8-on-ubuntu-20-04/](https://linuxize.com/post/how-to-install-php-8-on-ubuntu-20-04/)

---

### Post by satimis on 2023-02-14
> **SeijiSensei said:**
> Wasn't hard to find the answer: [https://linuxize.com/post/how-to-install-php-8-on-ubuntu-20-04/](https://linuxize.com/post/how-to-install-php-8-on-ubuntu-20-04/)
Hi,

Thanks for your link.

I have no problem upgrade php-7.4 to php-8.0 or to php-8.1 on Ubuntu 20.04 but the wp websites are running php-7.1.  After upgrade Ubuntu 20.04 to php-8.0/8.1 all wp websites are unable to work.  I'm searching whether there is a solution to upgrade the php version on all wp websites?

The wp websites are running on Ubuntu 20.04 VM.  I can export the Ubuntu 20.04 VM and then import the .ova image on Ubuntu 22.04 VM manager.  But all wp websites are unable to work because of in-match php version. 

Regards

---

### Post by garyed on 2023-02-15
I've had a similar problem with my websites not working going from php 7.4 to php 8.1. 
I found that there are errors in my php code that 7.4 allows but 8.1 will not allow.
If you haven't already done it, putting this code on your php pages might be useful to find out why they aren't working under php 8.1.
```
error_reporting(E_ALL);
ini_set('display_errors', '1');
```

---

### Post by satimis on 2023-02-15
> **garyed said:**
> I've had a similar problem with my websites not working going from php 7.4 to php 8.1. 
I found that there are errors in my php code that 7.4 allows but 8.1 will not allow.
If you haven't already done it, putting this code on your php pages might be useful to find out why they aren't working under php 8.1.
```
error_reporting(E_ALL);
ini_set('display_errors', '1');
```
Hi Gary,

Thanks your advice.

My cloned wp websites are running on Ubuntu20.04 VM with Ubuntu20.04 Host.  I performed following test:

1) Export the Ubuntu20.04 VM as .ova image
2) Import the .ova image to VirtualBox running on Ubuntu22.04 Host

Everything worked smoothly without problem.  All websites can be browsed on Ubuntu20.04 VM running on the new Ubuntu22.04 Host.

Now my nightmare comes.

3) Upgrade Ubuntu20.04 VM to Ubuntu22.04.  Again it went through without problem.  After finish;

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```

$ php --version```

PHP 8.1.2-1ubuntu2.10 (cli) (built: Jan 16 2023 15:19:49) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.10, Copyright (c), by Zend Technologies

```

Now I can't browse all websites because of different php version of the wp websites and Ubuntu22.04 VM.

4)
On browser running;
/ip-address/website_name/```

Your PHP installation appears to be missing the MySQL extension which is required by WordPress.

```

I can't start the website.

On Internet search all threads for its fixing found by me starts on the websites, running GUI.  But I couldn't start the website.  Unfortunately I haven't installed cPanel on Ubuntu20.04 VM.

I'm now searching document to fix the problem on Terminal of the new Ubuntu22.04 VM with commands.

That is my present situation.

Regards

---

### Post by garyed on 2023-02-15
I'm not familiar with VM or even how 22.04 reacts differently but there is always a possibility that it can add or delete things that can cause problems with php sites.  
I upgraded to php 8.1 & it caused problems with my website before I ever upgraded to 22.04 so for me it was definitely a matter of my php code & not the Ubuntu upgrade.
In your case if you're missing MYSQL then it might have somehow got deleted or some config file not upgraded correctly. 
You can always go to a terminal & do ```
mysql --version
``` to see if it's installed.
It might be easier to just reinstall MYSQL & see if that fixes things.

---

### Post by SeijiSensei on 2023-02-15
> Your PHP installation appears to be missing the MySQL extension which is required by WordPress.

```
sudo apt install php-mysql
```

You need the PHP module for MySQL. It must not have been loaded by default.

---

### Post by satimis on 2023-02-15
> **garyed said:**
> I'm not familiar with VM or even how 22.04 reacts differently but there is always a possibility that it can add or delete things that can cause problems with php sites.  
I upgraded to php 8.1 & it caused problems with my website before I ever upgraded to 22.04 so for me it was definitely a matter of my php code & not the Ubuntu upgrade.
In your case if you're missing MYSQL then it might have somehow got deleted or some config file not upgraded correctly. 
You can always go to a terminal & do ```
mysql --version
``` to see if it's installed.
It might be easier to just reinstall MYSQL & see if that fixes things.
$ mysql --version```

mysql  Ver 15.1 Distrib 10.6.11-MariaDB, for debian-linux-gnu (x86_64) using  EditLine wrapper

```

Regards

---

### Post by satimis on 2023-02-15
> **SeijiSensei said:**
> ```
sudo apt install php-mysql
```

You need the PHP module for MySQL. It must not have been loaded by default.
Performed step as advised.

$ sudo apt install php-mysql
$ apt policy php-mysql```

php-mysql:
  Installed: 2:8.1+92ubuntu1
  Candidate: 2:8.1+92ubuntu1
  Version table:
 *** 2:8.1+92ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status

```

On Firefox run;
/ip-address/website_name/```

Your PHP installation appears to be missing the MySQL extension which is required by WordPress.

```

Still the same error.

Regards

---

### Post by garyed on 2023-02-15
It might be a good idea to test a simple php page & see if it will work with your existing MYSQL database. 
I tried to post the code for a simple php page that would display the records from a database but I don't have permission to do so.
Anyways that might tell you if the problem is just with WordPress or not.

---

### Post by satimis on 2023-02-15
Hi all,

I solved the problem as follow;

$ php --version```

PHP 8.1.2-1ubuntu2.10 (cli) (built: Jan 16 2023 15:19:49) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.10, Copyright (c), by Zend Technologies

```

$ sudo nano /var/www/html/website_name/info.php
Enter following line on the file```
	
<?php phpinfo(); ?>

```

On Firefox run;
/ip-add/website_name/info.php

Look for```

Client API version  mysqlnd 8.1.2-1ubuntu2.10

```

$ apt policy php8.1-mysqlnd```

php8.1-mysqlnd:
  Installed: (none)
  Candidate: (none)
  Version table:

```

$ sudo apt install php8.1-mysqlnd```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'php8.1-mysql' instead of 'php8.1-mysqlnd'
php8.1-mysql is already the newest version (8.1.2-1ubuntu2.10).
php8.1-mysql set to manually installed.
The following package was automatically installed and is no longer required:
  gnome-tweaks
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Re-start VM

On Firefox run;
/ip-add/website-name/

Now all cloned websites on this VM can be started.

Remark:
It is quite strange to me.  I can't upload screenshot here.  I can select the screenshot but -> load without response

Regards

---

### Post by satimis on 2023-02-16
Hi all,

The steps mentioned on my postings #5 and #11 above are very convenient to move Ubuntu 20.04 VMs on an old PC to a new PC running Ubuntu22.04 VMs and Ubuntu22.04 Host

The steps work seamlessly.  I have completed moving 6 Ubuntu20.04 VMs without problem.

Regards

---


---
title: "How to tell apt-get that I already have it?"
date: 2007-09-13
forum: General Help
---

### Post by SitUbuSit on 2007-09-13
Hello,

I've installed a version of Zend PHP that came with it's own installer.  Now when I try to install other programs from the Synaptic Package manager or apt-get, that require PHP, I'm told that PHP will be installed.  How can I either tell Synaptic/Apt that I already have PHP or to exclude those packages from being installed?

For example,

```
$ sudo apt-get install phpmyadmin --dry-run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5 php5-common php5-mysql
Suggested packages:
  php-pear
Recommended packages:
  php5-mcrypt php4-mcrypt php5-gd php4-gd
The following NEW packages will be installed:
  libapache2-mod-php5 php5-common php5-mysql phpmyadmin
0 upgraded, 4 newly installed, 0 to remove and 42 not upgraded.
Inst php5-common (5.2.1-0ubuntu1.4 Ubuntu:7.04/feisty-security)
Inst libapache2-mod-php5 (5.2.1-0ubuntu1.4 Ubuntu:7.04/feisty-security)
Inst php5-mysql (5.2.1-0ubuntu1.4 Ubuntu:7.04/feisty-security)
Inst phpmyadmin (4:2.9.1.1-2ubuntu1 Ubuntu:7.04/feisty)
Conf php5-common (5.2.1-0ubuntu1.4 Ubuntu:7.04/feisty-security)
Conf libapache2-mod-php5 (5.2.1-0ubuntu1.4 Ubuntu:7.04/feisty-security)
Conf php5-mysql (5.2.1-0ubuntu1.4 Ubuntu:7.04/feisty-security)
Conf phpmyadmin (4:2.9.1.1-2ubuntu1 Ubuntu:7.04/feisty)

```

Looks like it would install PHP again if it weren't a dry run.  So, I tried adding a minus after the packages that I didn't want, and trying to force the install:

```
$ sudo apt-get -f install phpmyadmin libapache2-mod-php5- php5-common- php5-mysql- --dry-run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-php5 is not installed, so not removed
Package php5-common is not installed, so not removed
Package php5-mysql is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  phpmyadmin: Depends: libapache2-mod-php5 but it is not going to be installed or
                       libapache-mod-php5 but it is not installable or
                       php5-cgi but it is not going to be installed or
                       php5 but it is not going to be installed or
                       libapache2-mod-php4 but it is not installable or
                       libapache-mod-php4 but it is not installable or
                       php4 but it is not installable or
                       php4-cgi but it is not installable
              Depends: php5-mysql but it is not going to be installed or
                       php5-mysqli but it is not installable or
                       php4-mysql but it is not installable
E: Broken packages

```

But that does not seem to want to install anything, and seems to result in apt thinking things are broken.  What am I to do?

---

### Post by steveneddy on 2007-09-13
apt-get won't install anything that isn't already installed.

It may be trying to install a newer version than you already have installed.

:popcorn:

---

### Post by SitUbuSit on 2007-09-15
Thanks for the reply.  I don't think I was clear in my first posting:  The version of PHP that I installed was downloaded from Zend.com.  It's called Zend Core.  This version of PHP comes with it's own installer, so after installing it, if I bring up Synaptec package manager, it doesn't show any version of PHP being installed.  I don't fully understand all the differences between the Zend Core PHP files, and regular PHP, but I was interested in the Zend version because I can use a debugger with it, and I wanted to try out the Zend Framework which says it requires Zend Core.

Anyway what would be the best way for Ubuntu to keep track of PHP being installed?  Should I install the Ubuntu distribution of PHP and then install the Zend version over top of that or vice versa?

Is there a better way to debug PHP using the Ubuntu PHP distributions, and not messing around with this 3rd party installer?

---

### Post by steveneddy on 2007-09-16
Just install the php libs from Synaptic.

If you didn't get it from Synaptic or apt-get, then you won't see it as loaded in Synaptic.

synaptic is a list of AVAILABLE software ready to install, not what you actually have installed on your system.

For instance. I have Pidgen internet messenger installed on my laptop, but you won't find it in Synaptic because it isn't there. I DLed the raw file from the host web site and compiled it and installed it on my system that way. The old fashioned way. 

But, I install from synaptic and apt-get more often because it is easier and it is convenient.

:popcorn:

---

### Post by p_quarles on 2007-09-16
If I understand correctly, the problem is that you installed PHP from an alternate source, so APT doesn't know that it's installed. I did the same thing (didn't use zend, but compiled from source).

I think you have a couple options here:
1) Go ahead and install phpmyadmin from the repos, and then configure it so that it talks to the php installation you really want to use.

2) Compile phpmyadmin from the source code. I don't use this app, so I can't say for certain, but most source packages come with full instructions for integrating the installation with other relevant packages (which, obviously, would include php in this case). 

Using alternate installation methods has its ups and downs. Basically, choose your poison. :)

---


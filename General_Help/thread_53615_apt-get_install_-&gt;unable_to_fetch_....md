---
title: "apt-get install -&gt;unable to fetch ..."
date: 2005-08-01
forum: General Help
---

### Post by eeried on 2005-08-01
Hello,

I'm quite used to using apt-get, but I'm new to ubuntu.

I've checked the sources.list and I've di=one an apt-get update.

Installing Lynx is impossible : message is "unable to fetch some file : zise mismatch"

What's annoying is the downloads does take place (and takes all its time on a dial-up connection) and then the thing aborts. ](*,) 

Same with more complicated stuff -- though I had no problems at all with another Linux distro (Libranet). here's the complete apt-get install ouput:
```
$ sudo apt-get install php4-mysql mysql-server mysql-common mysql-client php4 phpmyadmin
Reading package lists... Done
Building dependency tree... Done
mysql-common is already the newest version.
The following extra packages will be installed:
  apache-common libapache-mod-php4 libdbd-mysql-perl libdbi-perl
  libnet-daemon-perl libplrpc-perl libzzip-0-12 php4-common
Suggested packages:
  apache apache-ssl apache-perl php4-pear dbishell libcompress-zlib-perl
  mysql-doc php4-gd php5-gd
The following NEW packages will be installed:
  apache-common libapache-mod-php4 libdbd-mysql-perl libdbi-perl
  libnet-daemon-perl libplrpc-perl libzzip-0-12 mysql-client mysql-server php4
  php4-common php4-mysql phpmyadmin
0 upgraded, 13 newly installed, 0 to remove and 13 not upgraded.
Need to get 3062kB/9802kB of archives.
After unpacking 27.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache-common libzzip-0-12 php4-common libapache-mod-php4 mysql-client
  mysql-server php4 php4-mysql
Install these packages without verification [y/N]? y
Get:1 http://archive.ubuntu.com hoary/main libnet-daemon-perl 0.38-1 [46.0kB]
Get:2 http://archive.ubuntu.com hoary/main libplrpc-perl 0.2017-1 [35.0kB]
Get:3 http://archive.ubuntu.com hoary/main libdbi-perl 1.46-4ubuntu1 [604kB]
Get:4 http://archive.ubuntu.com hoary/main libdbd-mysql-perl 2.9003-3 [130kB]
Get:5 http://archive.ubuntu.com hoary/universe phpmyadmin 2:2.6.1-rc1-1 [2247kB]Fetched 3046kB in 12m3s (4210B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/p/phpmyadmin/phpmyadmin_2.6.1-rc1-1_all.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Should I run --fix missing and what's the full command?

Or what should I do?

Many thanks in advance!

---

### Post by Xian on 2005-08-01
I would first just follow the advice it is giving you.
Open a terminal and enter the command below.

Then try to install the package again.

```
$ sudo apt-get update --fix-missing
$ sudo apt-get install php4-mysql mysql-server mysql-client php4 phpmyadmin
```

---

### Post by eeried on 2005-08-02
Okay, all solved!

The problem may have come from the fact I had a local repository that conflicted with the online ubuntu archives -- sticking with ubuntu repositories is definitely the right and only thing to do.

---

### Post by envis on 2008-02-14
thanks that fixed it! ( sudo apt-get update --fix-missing )

---


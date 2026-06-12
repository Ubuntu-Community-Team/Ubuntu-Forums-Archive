---
title: "MySQL 4.1.7 installation"
date: 2004-12-09
forum: General Help
---

### Post by Gataca on 2004-12-09
Is there somebody out there who is running Thunderbird MySQL 4.1.7 yet ? 
I downloaded the tar.gz package from the MySQL's site but no success on installing it ! 
-> Each time there is an error when I tried to run the server.

Is it possible to install it instead of the 4.0.20 version which is installed right now?

If so, can you explain to me how?

---

### Post by Gataca on 2004-12-13
Any idea ?  :sad:

---

### Post by p!=f on 2004-12-13
[QUOTE=Gataca]Any idea ?  :sad:[/QUOTE]
Thunderbird Mysql? Where did you download it from exactly?

---

### Post by Gataca on 2004-12-13
Let's forget Thunderbird. It's my mistake.

I'd like to install Mysql 4.1.7 instead of the ubuntu's MySQL 4.0.20
I downloaded it from www.mysql.com's site.

thanks for your help !

---

### Post by p!=f on 2004-12-13
Please post the error when you try to run the server here.

---

### Post by bpilgrim1979 on 2005-03-07
Yes, I have partially setup MySQL 4.1 run on Ubuntu.

First, I downloaded the binaries (not the RPM or apt-get).  Then I followed the instructions on this page:
[http://dev.mysql.com/doc/mysql/en/installing-binary.html](http://dev.mysql.com/doc/mysql/en/installing-binary.html)

So that worked for 4.1.x and I was able to login as root, set a root password, remove anonymous accounts, use test database, etc.  :) 

However, I have a few setup problems now that apparently the apt-get approach would have taken care of...
1) mysql isn't in $PATH, so I'm not sure where exactly to add that... .bashrc for root, for my user account, somewhere else...?
2) I'm not sure how to get MySQL to autostart.  I believe I might need to setup /etc/rc stuff.

Can anyone help on these two things?  Then MySQL 4.1 should work on Ubuntu... :)

---

### Post by p!=f on 2005-03-07
Could you explain why you did not use Debian packages? I'm afraid you're on your own if you want to compile it from sources by hand.

---

### Post by bpilgrim1979 on 2005-03-07
[QUOTE=p!=f]Could you explain why you did not use Debian packages? I'm afraid you're on your own if you want to compile it from sources by hand.[/QUOTE]

...because apt-get was for 4.0 and not 4.1 and certainly not for 4.1.10.  Does Ubuntu have 4.1 MySQL available via apt-get?

---

### Post by mpo on 2005-03-31
> Does Ubuntu have 4.1 MySQL available via apt-get?

Yes, at least in hoary: [http://higgs.djpig.de/ubuntu/www/hoary/misc/mysql-server-4.1](http://higgs.djpig.de/ubuntu/www/hoary/misc/mysql-server-4.1)

---

### Post by bpilgrim1979 on 2005-03-31
Add to sources.list:
deb [http://packages.dotdeb.org](http://packages.dotdeb.org) ./

apt-get update
apt-get install mysql-server-4.1

It's for woody.  I haven't tried this on ubuntu warty.

---

### Post by scence on 2005-06-01
[QUOTE=bpilgrim1979]Add to sources.list:
deb [http://packages.dotdeb.org](http://packages.dotdeb.org) ./

apt-get update
apt-get install mysql-server-4.1

It's for woody.  I haven't tried this on ubuntu warty.[/QUOTE]
this works for me. on warty.

---

### Post by bpilgrim1979 on 2005-07-25
Update:

mysql-server-4.1 is now [in universe](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mysql-server-4.1&searchon=names&subword=1&version=hoary&release=all).

> Package mysql-server-4.1

    * hoary (misc): mysql database server binaries [universe]
      4.1.10a-2ubuntu0.1: amd64 i386 powerpc
      4.1.10a-2: amd64 i386 ia64 powerpc
Installed it on hoary, along with mysql-administrator and mysql-query-browser.

---

### Post by ulrichvonbeck on 2005-08-11
I've got the 4.1 packages available, but I can't install any of them because of the following:

mysql-server-4.1:
 Depends: mysql-client-4.1 but it is not going to be installed
 Depends: libdbi-perl  but it is not installable

I've got the client and common files for mysql 4.0 installed, but there doesn't see to **be** a server for 4.0.

Is my situation salvageable from where I'm at now, or do I need to start uninstalling everything related to mysql and start over?

---

### Post by lenareea2065 on 2007-05-15
> **p!=f said:**
> Thunderbird Mysql? Where did you download it from exactly?


[memory Ebay Yahoo Loans music](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---


---
title: "Installing mysql WITHOUT Exim"
date: 2006-10-24
forum: General Help
---

### Post by emersony on 2006-10-24
Just as the thread title says, would like to (re)install mysql-server which inadvertantly got uninstalled. The problem is that both synaptic and aptitude want to install the exim suite which I don't need. qmail is running very well thank you, although synaptic of course only shows qmail-src as being installed, so basically it seems like apt thinks I need a mail program.

So how can I reinstall mysql-server without Exim? Planning on using something like vpop-sql. 

Also just wondering if  all the Deb based distos (Knoppix, Mepis, etc) have this forced dependency even if you have qmail installed?

puzzled,
Emerson

---

### Post by matthewstory on 2006-10-25
Grab the pre-compiled binary for linux from the mysql website and do it by hand, their documentation is very good on this point, and you will get around the exim4 dependancy in the package in the apt repository.  Afraid there's no way around this using apt.

---

### Post by Abhi Kalyan on 2006-11-04
Hmm interesting!

---

### Post by XtremXpert on 2008-02-29
Try using apt-get instead of aptitude

sudo aptitude install mysql-server-5.0

The following NEW packages will be installed:
  exim4 exim4-base exim4-config exim4-daemon-light libdbd-mysql-perl 
  libdbi-perl libhtml-template-perl liblockfile1 libmysqlclient15off 
  libnet-daemon-perl libplrpc-perl mailx mysql-client-5.0 mysql-common 
  mysql-server-5.0 

vs

sudo apt-get install mysql-server-5.0

Les NOUVEAUX paquets suivants seront installés :
  libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl
  libplrpc-perl mysql-client-5.0 mysql-common mysql-server-5.0

I also prefer aptitude, but for that issue, I'll use apt-get

---


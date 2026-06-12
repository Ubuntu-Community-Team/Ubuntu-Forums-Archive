---
title: "OpenLDAP Pain"
date: 2005-07-24
forum: General Help
---

### Post by jts on 2005-07-24
All,  
I've tried, but to no avail, to get openldap to compile on a clean Ubuntu system.
I'm trying to compile it based on instructions for an OpenXchange installation: [http://gpl.netixia.com/openxchange/openxchange-sarge-howto.html](http://gpl.netixia.com/openxchange/openxchange-sarge-howto.html)

Basically, you need it with "--enable-aci".

I get the slapd source, and do the "buildpackage" with fake root, resolve all the dependencies needed (libdb4.2-dev  libwrap0-dev libiodbc2-dev libncurses5-dev autoconf2.13 libgnutls11-dev #libgcrypt11-dev libltdl3-dev (>= 1.4.3) libslp-dev ), but then always end up with the following error chain:


/usr/lib/libsasl2.a(db_berkeley.o)(.text+0x5a): In function `berkeleydb_open':
: undefined reference to `db_create_4002'
/usr/lib/libsasl2.a(db_berkeley.o)(.text+0x85): In function `berkeleydb_open':
: undefined reference to `db_strerror_4002'


I've done some exhastive searches on google, but haven't turned up with anything that really solves my problem (or least that I can tell will :-)  ).

 ](*,) 


Has anyone had these problems and solved them?  


PS: Anychance on someone just packaging OpenXchange for Ubuntu?
PSS:  Ubuntu is fantastic and continues to amaze.

---

### Post by jts on 2005-08-01
I posted a message on the openldap mailing list (most referred me back to the Ubuntu forum for help).  I've got several helpful tips.

First, it was apparent that SASL2 was compiled to the Berkely DB libs, with a flag called: "unique name".  Therefore, I assumed 4002, links to any libbdb 4.2.

I installed it via Synaptic and did a grep on the libs for db_create_4002.  Bingo.

I still get the same errors in compilation though.  I'm assuming that the build of openldap is somehow finding a version of libdb that does not include this on my system.  I have 4.3 and 3 on my system, but cannot remove via Synaptic because of other major depency issues.


How do I force it to compile against the lib4.2 libraries and not the "first found"?

---

### Post by jts on 2005-08-02
Solved the problem.  

Note to Ubuntu Packagers, can a newer version of OpenLDAP be packaged?

I simply got the latest stable version of OpenLDAP and compiled it

./configure --enable-bdb --enable-aci --enable-crypt


No problems from that point on.

---

### Post by beej101 on 2006-03-19
im having the same problem... just wanted to know how you solved this? thanks!

---


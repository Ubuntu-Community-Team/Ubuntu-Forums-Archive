---
title: "libldap-2.4-2 mess in Utopic"
date: 2015-04-12
forum: General Help
---

### Post by petran79 on 2015-04-12
I did the upgrade from 14.04 to 14.10 so as to move to 15.04 in a few days. 
Unfortunately some critical libraries are messed after the update.

most notable is the file libldap-2.4-2

I am unable not only to install applications like Wine, but also other programms. It gives me dependencies errors

 
some steps I did:
[B]
apt-cache policy libldap-2.4-2

installed: 2.4.31-1+nmu2ubuntu12
 candidate: 2.4.31-1+nmu2ubuntu12
  version table:
 *** 2.4.31-1+nmu2ubuntu12 0
        100 /var/lib/dpkg/status
     2.4.31-1+nmu2ubuntu11 0
        500 [http://ftp.ntua.gr/pub/linux/ubuntu/](http://ftp.ntua.gr/pub/linux/ubuntu/) utopic/main amd64 Packages[/B]

[B]dpkg -l | egrep "libldap|ldap-utils"
ri  libldap-2.4-2:amd64    2.4.31-1+nmu2ubuntu12    amd64  OpenLDAP libraries
rc  libldap-2.4-2:i386   2.4.31-1+nmu2ubuntu12  i386 OpenLDAP libraries

sudo dpkg --print-foreign-architectures
i386
[/B]

now when I want to install an application, eg Wine 1.6 from Ubuntu repo or even the Wine PPA, I get this error, even with sudo apt-get install -f

**libldap-2.4-2 : depends on: libgnutls-deb0-28 (>= 3.3.0) but 3.2.16-1ubuntu2.2 is about to be installed**

Now 3.3.0 release is only for 15.04, while 14.10 has 3.2.16-1ubuntu installed. 


Also when I open Software Center it gives me an error that software cant be installed. If I click the button to fix it I get this message:

[B]ibldap-2.4-2: Depends: libc6 (>= 2.14)  but 2.19-10ubuntu2.3 is installed
               Depends: libgnutls-deb0-28 (>= 3.3.0) but 3.2.16-1ubuntu2.2 is installed
[/B]

Software Center crashes too.

While I was able to remove the 386 versions of lbldap-2.4-2 and lbldap-dev to fix the error in libcurl3 package, removing the amd64 version is out of the question since it will remove the whole software library.
I hope that  updating to 15.04 will fix this issue. Till then are there any other solutions? Things seem to be messed up

---


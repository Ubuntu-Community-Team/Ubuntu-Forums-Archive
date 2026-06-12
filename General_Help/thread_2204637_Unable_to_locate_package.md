---
title: "Unable to locate package"
date: 2014-02-09
forum: General Help
---

### Post by Philip_James on 2014-02-09
Hi Everyone!

I am running Ubuntu server 12.04 (fully updated) and am playing around with joining it to an active directory domain.

I need to install a package called libnss-winbind however when I run 'sudo apt-get install libnss-winbind' I get an error return stating 'E: Unable to locate package libnss-winbind'

I have checked to make sure all entries in the /etc/apt/sources.list ending with 'universe' are not commented out but still I get this error.

Bit of a newbie here, apologies in advance!

I am trying to follow the steps in this [link ]("http://phreek.org/guides/ubuntu-samba-active-directory-member-server")

Thanks for reading!

---

### Post by Doug S on 2014-02-09
It looks to me as though that package is not part of the 12.04 packages. It is there for 12.10 onwards though.

---

### Post by Frogs Hair on 2014-02-09
I located this question. [https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/194932](https://answers.launchpad.net/ubuntu/+source/ia32-libs/+question/194932)

---

### Post by Philip_James on 2014-02-09
Thanks for the updates guys, much appreciated!

I have managed to work past this error. I think that this package must have (in some form) been part of all the updates that have been installed, and by running the command 'sudo apt-get install -y ntp krb5-user samba winbind libpam-winbind' everything I need has been installed and configured.

My Ubuntu server is now part of my Windows Server 2012 domain AND I can managed share permissions and file security on the Ubuntu box from Windows!

Thanks again!

---


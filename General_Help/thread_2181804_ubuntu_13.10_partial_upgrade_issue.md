---
title: "ubuntu 13.10 partial upgrade issue"
date: 2013-10-19
forum: General Help
---

### Post by hunterkasy on 2013-10-19
I am running 13.10 64 (since beta) and when I try to use the software updater I get the partial upgrade to display so I click on partial upgrade and then I get this:
can not upgrade
an upgrade from 'trusty' to 'saucy' is not supported with this tool 

what can I do to force it to upgrade or whatever it needs to do?

thanks

---

### Post by PJs Ronin on 2013-10-19
If I remember correctly, the 'partial upgrade' option is one that should not be taken as there may be some dependency issues that end up borking your system.   Best to use "sudo apt-get update" and "sudo apt-get upgrade" in terminal.

---

### Post by grahammechanical on 2013-10-19
I just click on "Continue" and after a few seconds Updater Manager works as normal. In fact it is usual to get this "partial upgrade" offer when using the development branch. It will appear and not appear several times over the development cycle. Another error we may get is a warning that there is something wrong with our Internet connection when in fact there is nothing wrong with it. The problems lies with having PPAs that are no longer maintained or not available for the development branch.

Regards.

---

### Post by Sudo_SU_Root on 2014-01-09
The reason I was offered this Partial Upgrade is because I use debootstrap to create a 'raring', or other version, minimal base, to use with Docker [http://docker.io](http://docker.io)  a.k.a. lxc-docker

I do not want to log into my desktop with thise minimal builds, which is why it was offering the partial upgrade, so I just click continue and then install all but that package, which is unchecked if you click continue, because it is for another build version.

---


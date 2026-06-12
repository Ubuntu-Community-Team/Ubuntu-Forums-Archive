---
title: "Installing alien on Ubuntu 13.10 64bit"
date: 2013-10-18
forum: General Help
---

### Post by Jacob_Tennant on 2013-10-18
I am trying to install alien 8.99 on my fresh 13.10 system.

I run "sudo apt-get install alien" and the system replies that there is no package named "alien"

I have downloaded a .deb of alien but it won't install either as it states missing depedency of "debhelper", when I downloaded the .deb of debhelpers it too has missing dependecnies...

All I am trying to do is to install Oracle XE 11g express so I can begin to learn SQL.

HELP

---

### Post by cboschmans on 2014-03-20
Hi,

Has anyone got a solution to this problem ?

---

### Post by philinux on 2014-03-20
> **cboschmans said:**
> Hi,

Has anyone got a solution to this problem ?

According to this alien 8.89 is in the saucy repo.

[http://packages.ubuntu.com/saucy/alien](http://packages.ubuntu.com/saucy/alien)

Should be easy to install from synaptic, SC or terminal.

---

### Post by su:bhatta on 2014-03-20
> **Jacob_Tennant said:**
> I am trying to install alien 8.99 on my fresh 13.10 system.

I run "sudo apt-get install alien" and the system replies that there is no package named "alien"

I have downloaded a .deb of alien but it won't install either as it states missing depedency of "debhelper", when I downloaded the .deb of debhelpers it too has missing dependecnies...

All I am trying to do is to install Oracle XE 11g express so I can begin to learn SQL.

HELP

You can install a small program called GDebi through Software Center and use GDebi to install the Deb file of Alien you have got.
Sometimes Software Center cannot resolve dependencies well, but GDebi is a better tool at installing Deb files.

---


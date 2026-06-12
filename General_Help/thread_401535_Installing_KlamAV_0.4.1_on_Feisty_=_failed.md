---
title: "Installing KlamAV 0.4.1 on Feisty = failed?"
date: 2007-04-04
forum: General Help
---

### Post by Lucifiel on 2007-04-04
Hey, I've been trying to install Klam AV 0.4.1 on Feisty.

However, I keep getting this message:

> ***** Dazuko
***** Running configure (./configure)...
checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (cc)
kernel source in /lib/modules/2.6.20-12-generic/source... no
kernel build source in /lib/modules/2.6.20-12-generic/build... yes
kernel source in /lib/modules/2.6.20-12-generic/build... yes
acquiring Linux kernel code configuration... error
error: unable to compile linux_conf utility
please see `linux_conf_make.out' for details
***** Return value 1

I've sought to search the net for information on linux_conf but couldn't find much about this.

---

### Post by Jupp on 2007-04-28
Hi,

I had the same problem. Loading the source with synaptic will not work. Go to [www.dazuko.org](www.dazuko.org) and download the latest version. (dazuko-2.3.3) Then compiling should work.
I have another problem with dazuko: insmod will not work, giving always the error message:  error inserting ./dazuko.ko -1 invalid parameters.

---

### Post by camelean on 2007-09-17
wondering if you found a fix to not being able to insert dazuko.  I'm having the same issue can't seem to find the answer. (feisty 2.6.20-116)

---


---
title: "ubuntu slow in responding"
date: 2007-08-04
forum: General Help
---

### Post by ubghertzx on 2007-08-04
hi i had installed a  Ubuntu 7.04 - the Feisty Fawn.... but everything is slow in starting up... even the terminal takes about a minute to load.... i checked the system monitor but it doesnt show any heavy load...
i have 512 mb mem...
can anyone pls help.....

---

### Post by gmaniac on 2007-08-04
check  sudo hdparm /dev/hda (hda is the drive i've installed ubuntu, yours could be ie hdb )
and see if you get something like this

 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)

also maybe you are having problems with desktop effects.Try to disable it.
post the output of ```
dmesg
```, and ```
ps aux
``` commands.

---


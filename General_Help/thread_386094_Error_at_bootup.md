---
title: "Error at bootup"
date: 2007-03-16
forum: General Help
---

### Post by sjpritch25 on 2007-03-16
I get the following error at boot up

BusyBox v1.13 (debian 1:1.1.3-2ubuntu3) Built in shell (ash)

/bin/sh: can't access tty : job control turned off



Please help!!!!!  I am fairly new to linux and don't know what this means.   

Thanks.

---

### Post by Arby on 2007-03-17
Hi,

A lot of people seem to be getting this error lately, I wish I knew what causes it. [This  thread]("http://www.ubuntuforums.org/showthread.php?t=384031&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty") reports the same error and they seem to have fixed it. So you might want to have a look at the instructions there. It seems to be something to do with grub getting confused about the order of partitions/drives but I haven't figured out more than that yet. If you need more help, just ask.

Arby

---

### Post by sjpritch25 on 2007-03-17
Thanks for the link.  I fixed it.   Boy, what an easy fix.  I just had to switch my SATA cables and it worked.

---


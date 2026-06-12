---
title: "&quot;*ERROR* EIR stuck: 0x00000010 ma&quot; during boot"
date: 2014-04-20
forum: General Help
---

### Post by drofart on 2014-04-20
I have just installed Ubuntu 14.04 on my Dell Vostro 1015 laptop, and  now I am getting an error during boot-up that says something like: ******ERROR* EIR stuck: 0x00000010,*** I searched a bit, and found that it is a problem with the graphics processor or something like that but i am not sure. What is it?

below are some info regarding my system

[HTML]$sudo dpkg -l | grep video-intel**
ii  xserver-xorg-video-intel 2:2.99.910-0ubuntu1 i386         
X.Org X server -- Intel i8xx, i9xx display driver

$lsb_release -a**
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:   trusty

$uname -a**
Linux mrinal-Vostro-1015 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 
UTC 2014 i686 i686 i686 GNU/Linux

$sudo lspci | grep VGA**
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset
Integrated Graphics Controller (rev 07)[/HTML]

---

### Post by drofart on 2014-04-21
Hello,
  I tried a workaround by adding "i915.modeset=0" to "GRUB_CMDLINE_LINUX_DEFAULT", tho it stoped the error but my resolution dropped to 1024x786 which is not normal.

Any idea folks???

---


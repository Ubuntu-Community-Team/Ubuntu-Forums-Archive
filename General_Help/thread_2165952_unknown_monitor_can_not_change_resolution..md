---
title: "unknown monitor can not change resolution."
date: 2013-08-07
forum: General Help
---

### Post by sirtcp on 2013-08-07
my monitor is unknown and i can not go above 1027x768 resolution

my VGA
/home/admin# lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])

My Motherboard

dmidecode | grep Product
Product Name: DZ68DB


in installed. 
apt-get install xserver-xorg-video-intel
apt-get install xserver-xorg-core

i am using GDM 

my LCD can support 1440x900.

i tried altering /etc/X11/xorg.conf

i followed many howto on internet for editing and reconfiguring xorg.conf but none of them help so finally i am asking the community.

any help will be highly appreciated. 

Thanks,

Myk

---

### Post by oldos2er on 2013-08-07
Which version of Ubuntu are you using?

---


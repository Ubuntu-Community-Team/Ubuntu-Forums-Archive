---
title: "screen settings lost ater reboot"
date: 2005-03-22
forum: General Help
---

### Post by pieter hollenberg on 2005-03-22
hoary is almost perfect for me (and for my friends of cours)

up till now, I only have a few problems:

1-I have to set the resolution/refesh rate every time again because these settings are lost after every reboot 

2. hoary gives me only the refresh rate 75 Hz, but onder windows xp it can be set to 100Hz. (I have XP and Ubuntu dualboot)

how can I solve this ?

ASUS CUBX
P3 733
Nvidia TNT2 M64 pro

---

### Post by bored2k on 2005-03-22
[QUOTE=pieter hollenberg]hoary is almost perfect for me (and for my friends of cours)

up till now, I only have a few problems:

1-I have to set the resolution/refesh rate every time again because these settings are lost after every reboot 

2. hoary gives me only the refresh rate 75 Hz, but onder windows xp it can be set to 100Hz. (I have XP and Ubuntu dualboot)

how can I solve this ?

ASUS CUBX
P3 733
Nvidia TNT2 M64 pro[/QUOTE]
 First of all when picking resolution, do not select make default for computer , because that will reset it .

Try reconfiguring xorg [worked for me] by typing:
 sudo dpkg-reconfigure xserver-xorg

---

### Post by pieter hollenberg on 2005-03-23
the reconfigure command did it.

thanx !

(only 85 Hz but that's sufficient for me)

---


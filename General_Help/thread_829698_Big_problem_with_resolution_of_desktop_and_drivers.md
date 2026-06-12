---
title: "Big problem with resolution of desktop and drivers"
date: 2008-06-15
forum: General Help
---

### Post by radial on 2008-06-15
Hello and sorry for my English.
Recently, I format the hard disk and changed Ubuntu 7.10 to 8.04 and during the fresh configuration, I met a problem. It is that when I start my graphics card drivers from: nvidia-glx-new or nvidia-glx-new-enva, the resolution of my desktop changes to 640x480 and I can not make it higher. Editing xorg nothing helps. My graphics card is Nvidia GeForce 7300 GT. At the Ubuntu 7.10 worked well. 
Please help!

---

### Post by richardmems on 2008-06-15
i also having problem with 8.04

on-board vga (unichrome integrated graphics) seems now working properly. getting dual line distorted images on GUI interface beginning from the installation environemnt and after installation also..

pls let me know how can i edit xorg to fix it..

thanks
richards

---

### Post by radial on 2008-06-15
I read post [http://ubuntuforums.org/showthread.php?t=808172&highlight=7300](http://ubuntuforums.org/showthread.php?t=808172&highlight=7300) and I used the command to change drivers from nv to nvidia. > sudo displayconfig-gtk

For any change to the driver "nvidia" exchanged resolution to 640x480.

---

### Post by radial on 2008-06-15
So can someone help me or I'm sentenced to windows?
I beseech for help!

---

### Post by Pjotr123 on 2008-06-15
This will probably help:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by radial on 2008-06-15
oh.. my god it's work!! Thanks very much man...

---


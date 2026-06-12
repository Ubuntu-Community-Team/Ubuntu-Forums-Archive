---
title: "How to check, if any of the following is ON?"
date: 2006-09-11
forum: General Help
---

### Post by Thanatios on 2006-09-11
Well my ubuntu is rather slow right now.
Running on a:
Pentium 3 800 MHZ PC
512 MB RAM
NVIDIA RAVE TNT2

so how to check if anything of the following is on?

3d video acceleration
DMA

Thanks in advance!

---

### Post by madmetal on 2006-09-11
try
sudo hdparm /dev/hdc 
to see about hdd infos and dma
about 3d i dont know.. i run a 3d screensaver and see the fps but thats not accurate :-\" :-\"

---

### Post by Bagnaj97 on 2006-09-11
To test if 3d acceleration is enabled type ```
glxinfo | grep direct
``` If acceleration is enabled then it will say direct rendering: yes

---

### Post by madmetal on 2006-09-11
thanx! rendering:yes

---

### Post by Thanatios on 2006-09-11
Well, I get the following:

thanatios@thanatios-desktop:~$ glxinfo | grep direct
direct rendering: No
thanatios@thanatios-desktop:~$ sudo hdparm /dev/hda | grep using_dma
Password:
 using_dma    =  1 (on)

Any idea how to get turn Direct Rendering on?
Thanks in advance

---

### Post by Ramses de Norre on 2006-09-11
Give some more info, video card type and such.

---

### Post by ~LoKe on 2006-09-11
I'd like to know how, as well.  My card is an nVidia Geforce 4 MX420.

**EDIT:** If I recall correctly, I used to have it enabled, but I've recently used the Envy script to get the latest drivers.  Perhaps that turned it off?

---

### Post by Bagnaj97 on 2006-09-12
> **~LoKe said:**
> I'd like to know how, as well.  My card is an nVidia Geforce 4 MX420.

**EDIT:** If I recall correctly, I used to have it enabled, but I've recently used the Envy script to get the latest drivers.  Perhaps that turned it off?

To enable 3d acceleration on NVidia cards read these instructions [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) If you need more help give me a shout.

---

### Post by az on 2006-09-12
> **Thanatios said:**
> Well my ubuntu is rather slow right now.


What does slow mean to you?

---


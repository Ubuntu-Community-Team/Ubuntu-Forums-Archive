---
title: "Ubuntu Studio won't boot, stalls at timidity"
date: 2007-11-10
forum: General Help
---

### Post by GinKen on 2007-11-10
Having a bad day here.  Intentions were good.  Wanted to help a friend by installing Ubuntu Studio Gusty 64-bit on his Dell Inspiron 1721, both because he wants eventually to do some video work and because he was exicited to learn there were options to Windows and wanted to try Ubuntu.  Problem is sound card trouble, per [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) , but, where ordinary Gusty 7.10 apparently boots fine but has sound problems, UbuntuStudio with its rt kernel will not even boot completely, but startup stalls with timidity, red fail.
I can get into recovery mode, and here have tried the various fixes found in these forums, including compiling the latest 1.0.15 alsa drivers, but to no avail.
I installed oss v4, which provides sound, but still can't startup past timidity, as it seems timidity is interwoven with alsa.  
Has anyone found a way around this?  Is it possible to set timidity to work with oss v4?
My other options seem to be to install and boot from the generic kernel until there is a fix so the rt kernel works, or do a clean install of Gusty, and wait for better days before trying to install Ubuntu Studio again.  Here are a few specs:
Dell Inspiron 1721 
SigmaTel STAC9205
lspci -v shows audio device: ATI Technologies Inc SBx00 Azalia
aplay -l reports "no soundcards found"
Any input or feedback welcome!

---

### Post by botezuma on 2007-12-03
I have almost the same problem, I have installed Ubuntu Studio packages over 7.10 and now I can't play sound and besides this the network interface doesn't work. I had to modify grub to boot the generic 7.10 kernel. It works fine but stalls at timidity for about 30 secs. Running on a Dell Inspiron 6400 with the same sound card.

---

### Post by Vimana on 2007-12-16
Same problem here. Boot stops at "timidity". Dell Inspiron 5160.

Vi

---


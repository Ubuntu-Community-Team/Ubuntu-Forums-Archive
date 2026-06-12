---
title: "NeroLINUX"
date: 2005-09-22
forum: General Help
---

### Post by Mr Frosti on 2005-09-22
Has anyone had experience with this application? You can download a .deb from [http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)

I have NeroLINUX 2.0.0.1 running on Ubuntu 5.04 (build on top of Debian) and I am having the following issue.

Burning a .nrg image has completed successfully all 9 times I have tried it. This is with two different .nrg images. Burning a .iso file has failed both times I have tried it. The burn process starts the same as with a .nrg image, but it gets to 5% and then the program locks up. I can't stop the burn, and I can't kill the program. It just keeps clicking the CD in my CD drive.

I am not having any other issues as far as I know. Phenominal program though, I am really happy they decided to make a Linux client. It just needs some bugs worked out before it is ready for the mainstream.

---

### Post by skoal on 2005-09-22
I haven't had much experience using NeroLinux.  But, just a few things you might want to try:

1. Make sure that you are not using the 'ide-scsi' module, especially as a grub kernel boot time option.  That thing is deprecated, and I don't even know if that comes with a stock hoary install (since I use a custom kernel). 

2. Try dropping the writing speed a notch.

Just stabbing at the dark, here...

\\//_

---

### Post by jeremy on 2005-09-23
Have you enabled DMA for your writer?

I have tried Nero Linux, and found it seriously lacking in respect to, say, K3b, apart from the fact that it is not free (in either sense of the word!).

---

### Post by Mr Frosti on 2005-09-30
If I don't have DMA enabled for my CD-ROM drive, it does not even detect it as an available option. I have tried K3B and really support it. Yes, it is a superior product. I do want to try and support a company that releases software on Linux however, and I was just giving them a fair shot. 

Thanks for the advise, I will try these things...

---

### Post by patrick295767 on 2005-09-30
If a choice has to be made between : 

gnomebaker 

K3B

nero linux 


====> Would it be : K3B best burning program in Linux ?

---

### Post by duffydack on 2005-10-06
I have to use nero linux, as k3b does not let me write multisession dvds with my Sony DW-D56A( Liteon slimtype).  WOrks fine in windows for everything but k3b refuses to append data saying my writer is not capable of incremental streaming, and only overwrite mode, which just overwrites (believe it or not :) ) so for now, nerolinux works fine and dandy for me.

---

### Post by Ryujin on 2005-10-06
I have had a lot of luck with Nero Linux where gnome baker failed, but k3b is still my favorite, the big benefit with Nero Linux is that it uses its own libraries and therefore performs well with tasks that may be failing with gnome baker.

---

### Post by cvmostert on 2005-11-02
I JUST installed nerolinux, sad that it is not free... but gnomebaker is really losing my attention...

---


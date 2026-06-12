---
title: "libdvdcss2 in Edgy problems"
date: 2007-01-04
forum: General Help
---

### Post by cor2y on 2007-01-04
is there something wrong with the way edgy processes libdvdcss2? I tried compiling and even using the deb from Automatix and easy ubuntu and saveas´ repo but my commercial dvds all stop when they have to access the second layer ( at least i think its the second layer i´m not sure) , halfway through a movie it stops and up pops a message that its encrypted and i need libdvdcss.
This happened in both totem,mplayer and gxine with the xine-lib backend.
I tried it in vlc and the same result except there was no popup message, vlc just stopped playing at the same position as all the others.
If it was a specific disc then i´d think it was related to how it was authored or that it was damaged in some way, however all of my commercial dvds are having this problem.

Finally i broke down and installed lindvd something i was hoping to avoid.
The damned thing made me set a region for it to play the disc, something i hoped to never see again in linux.
The dvds of course all played through to the end with no problem in lindvd so the culprit is either the edgy version of libdvdcss2 or something in the way the discs are being read from layer to layer or my install is bonked somehow.

I never had this problem in Dapper by the way and Edgy was installed clean the only thing that came over from Dapper was my home directory.

---

### Post by riven0 on 2007-01-04
Can you try inputting this in the terminal and see if it makes a difference?:

> sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh

---

### Post by cor2y on 2007-01-04
Thank you riven0 that seems to have done the trick , just tried 3 different dvds at the chapter stops where the popup message occurs and they play through.
I already had libdvdread3 install to remove it would have resulted in some loss of packages.

However i am being urged to update my version of libdvdcss2, something i won´t do so it seems the error does indeed lie with the latest edgy version.


Now i can uninstall lindvd.

---

### Post by fragos on 2007-01-04
I installed package libdvdcss2 from the Ubuntu repositories with Synaptic and haven't seen the problem you've had.  I recommend people use Synaptic and the Ubuntu repositories before resorting to compiles and the likes of Automatix, EasyUbuntu and 3rd party repositories.

---


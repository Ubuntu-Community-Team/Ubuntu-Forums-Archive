---
title: "WUBI and MBR"
date: 2007-09-22
forum: General Help
---

### Post by cliff0108 on 2007-09-22
I endeavored to install Wubi on my wife's computer running Win98 and kept getting an error message that I should download an alternate ISO - although there were no directions as to _which_ 'alternate ISO'. 

Not having a lot of time to play with this I proceeded to uninstall Wubi from add/remove and did so.
HOWEVER when I reboot it goes to a black screen giving me: options to boot: 1. Window 2. Ubuntu . 

What is going on - did Wubi re write the MBR and if so how do i get things back to normal ?

And - for that matter - what would have been the 'alternate ISO' I should download.

Thanks
Cliff

---

### Post by Sturmeh on 2007-09-22
The alternate iso it requires you to use is the "non-liveCD" version.

Wubi should automaticly download this, and it is only 700MB, so let it download when appropriate ( off-peak etc. ) then it will proceed to installation.

IF for some reason you cannot download it using normal conventions...
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)
That is the latest alternate release ( for 32bit ) ...

You are on Win98, the MBR is left untouched, only the boot loader in win98 would haave been touched, and it will be completly restored when you uninstall wubi.

Good luck!

---

### Post by cliff0108 on 2007-09-22
Thank you so much for your comprehensive and speedy reply !
I think I will re-try the install with the alternate ISO. I presume I just put the ISO file in the install subdirectory and it will do it's thing ? I don't have to create an installtion disk or anything?
Cliff

---

### Post by cliff0108 on 2007-09-23
I downloaded the ISO as per the link and put it in the wubi/install folder and then ran wubi install gain. Same error message to "down load the alternate iso"
What am I doing wrong here ?
I tried the uninstall again and still get the same balck screen 2 option boot screen.

---

### Post by ago on 2007-09-24
That's a bug fixed in the new release (7.10). But that is still experimental

---


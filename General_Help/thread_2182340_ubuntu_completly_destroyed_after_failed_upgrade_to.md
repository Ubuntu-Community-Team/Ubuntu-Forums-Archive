---
title: "ubuntu completly destroyed after failed upgrade to 13.10"
date: 2013-10-20
forum: General Help
---

### Post by crazymonkey05 on 2013-10-20
so today i attempted to update to ubuntu 13.10 after being on ubuntu 13.04 and about midway through the first part of the upgrade my home had a black out and the PC lost power now after meny very aganizing attempts to get ubuntu started i just give up....

so here is what happens when the pc powers on.

1) BIOS starts and does self test
2)starts ubuntu boot process
3)grub give the choice of what to do
4)normal ubuntu splash starts then goes to black screen with a frozen cursor at the top left of the screen.

What i have tried to fix it

1) did a full upgrade using command ```
sudo apt-get upgrade
``` this got it up to ubuntu 13.10 however no DM or GUI of any kind will load

2) install unity again using command ```
sudo apt-get install unity
``` this caused the whole system to freak out i cant even get to a root shell now. :(

so if there is any other info you need just ask and i will try and get it. (BTW i have ubuntu 13.10 on a live usb so if i need it i can use it)
also if there is a way to install ubuntu 13.10 without formating the drive i will gladly welcome input about that thanks again.

---

### Post by Allavona on 2013-10-21
Use the LiveUSB to chroot into your installation. This is a tuxgarage link thats from 2011. Not only does it save me a ton of typing, its right up your alley, loss of power and all!

[http://www.tuxgarage.com/2011/07/creating-chroot-ubuntu.html](http://www.tuxgarage.com/2011/07/creating-chroot-ubuntu.html)

---

### Post by crazymonkey05 on 2013-10-21
thanks for the links i will try when i get home and hopefully get my install started again. :)

---

### Post by philinux on 2013-10-21
> **crazymonkey05 said:**
> thanks for the links i will try when i get home and hopefully get my install started again. :)

Once in the chroot you can do a 

sudo dpkg --configure -a

Although sudo not needed in a chroot.

---

### Post by crazymonkey05 on 2013-10-24
ok thanks everyone for the help after i got in and chrooted here is what i did:

1) attempted a chroot fix and repair.(FAILED)
2) attempted a reinstall without touching personal files (WORKED)(however i had problems with the install as it detected it as a temp install? :confused:)
3) Gave up and just formatted and reinstalled the system (WORKED)

thanks everyone for your wonderful input i forgot i had everything backed up to ubuntu one so i am all right,thanks again. i will mark this thread as solved

---


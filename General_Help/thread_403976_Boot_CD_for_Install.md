---
title: "Boot CD for Install"
date: 2007-04-07
forum: General Help
---

### Post by infinitelink on 2007-04-07
So I got this guy, a cousin, a great guy: with a broken box-poor guy. Anyways, his computer won't boot from disc: we got it working from Floppy, but not disc. 

With Windows it's possible to use a windows floppy to point at the setup file on the CD and force the computer to do the install. How do we do this with linux EASILY? We don't have incredible computer skills here, we're just trying to get an old computer to run again.

Yes we did check the boot-order and CD is at the top.

Anyways, we need help with getting a boot-disk and then how to create it on a floppy, and then what command to enter if the CD is on the floppy. I hope this is possible. Thanks for all help in advance. 

: )

inLiNk

---

### Post by cantormath on 2007-04-07
have you gone into the bios and checked to see if the cd is first in the boot order..?

you need to do this if you want the computer to boot to cd first.

---

### Post by dark_nny_jthm on 2007-04-07
Hello this is infinelink's cousin and yes we have Bios first boot device set as CD.

---

### Post by dark_nny_jthm on 2007-04-07
bump

---

### Post by cantormath on 2007-04-07
k.............hmmmm.  first, I would reset the bios (restore default) and save.  Then change the boot order to cd.  Then disable any of the logo screens that might be shown while booting (ie dell Globe).  You want to see all info while booting.  there might be an option when booting to hit a key(like F12) to choose boot drive, or hit any key to boot from cd.  Another Option, if this does not resolve things, is to try the alternative cd.  Also make sure that you are using the correct install cd(X86, ppc , 64bit etc).  

Start there.

---

### Post by dark_nny_jthm on 2007-04-07
Ok I've done that and none of that works.... not resetting  and the only CD I have I guess relies on windows to install.... is their a way that i can tell DOS to use the CD to install? I can get DOS to work and my A drive to work that's about it... i can also get you info about my PC if you need it...

---

### Post by cantormath on 2007-04-07
> **dark_nny_jthm said:**
> Ok I've done that and none of that works.... not resetting  and the only CD I have I guess relies on windows to install.... is their a way that i can tell DOS to use the CD to install? I can get DOS to work and my A drive to work that's about it... i can also get you info about my PC if you need it...

WOOH!.........think we are crossing some signals here.  Nothing relies on windows to install.  You need to put the cd in the disk drive and reboot so that the cd boots instead of windows. Windows will never know what hit it. Windows never knows anything until it is loaded.

You also do not use dos in any kind of installation when it comes to linux.  

There are two ways.
1) use an installation cd and booting to the cd instead of into windows. (RECOMMENDED)
2) download the Ubuntu installation Script for windows. ( I have never tried it so I dont know how effective this, I probably should not even mention it)
[http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

### Post by dark_nny_jthm on 2007-04-07
Well that's the thing... I can't get the CD to boot...sorry about the whole "i guess it relies on windows" thing...I didn't realize people were so touchy about it..anyways I guess my problem really is I can't get my PC to boot CDs..anyway you can help me with that? Also I don't have windows currently installed for the reason that my PC wont accept CDs period...

---

### Post by az on 2007-04-07
sbm is on the install disk.  It is in the install folder.  Write it to floppy (read the txt file or download rawrite for windows and put it on a floppy.

Boot the floppy.  Wait untill it probes your hardware.  It will present you with a list of bootable devices.  Pick your cdrom (you need to call up the menu - I forget which keys you press, but you select "boot it" and sbm will boot your cdrom.

It's made for machines who's bios cannot boot from cd.

---

### Post by dark_nny_jthm on 2007-04-07
How would I enable sbm in the install folder...I'm sorry if I seem totally devoid and confused hear but I am... the rawrite says it needs windows32  and I don't have it on my PC. :confused: Tomorrow I plan to look at my PC and see if we connected the CD drive back right....even in DOS it says it cant find my cd-rom drive so I'm wondering if its that....

---

### Post by az on 2007-04-08
> **dark_nny_jthm said:**
> How would I enable sbm in the install folder...I'm sorry if I seem totally devoid and confused hear but I am... 

You boot a floppy.  The floppy has sbm on it.

---


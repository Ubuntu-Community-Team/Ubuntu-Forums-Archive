---
title: "Installed Vista AFTER Ubuntu"
date: 2007-02-22
forum: General Help
---

### Post by betawind on 2007-02-22
Howdy,

I installed Windows Vista after running Ubuntu 6.10 for the last 4 or so months.  I knew this would overwrite GRUB but I figured I could just repair it afterwards.  While the repair was successful (did it from an Ubuntu 6.10 Live CD), it did not seem to fix GRUB.  When the system boots up, it still goes directly to Vista.  I have tried using the Super GRUB disk to fix the MBR but again to no avail.  I can, however, use the GRUB disk the load GRUB and boot into Linux, so I know GRUB itself works and my Linux partition is in tact.  Any thoughts?

Btw, my disk setup is as follows:

hd0 - Ubuntu
hd1 - Vista
hd2 - Media Drive


Thanks in advance,

Beta

---

### Post by GameManK on 2007-02-22
When you reinstall grub does it give you a choice of where to install it?  You want to install it to the MBR.

---

### Post by betawind on 2007-02-22
When I installed grub using the super disk I did specifically tell it to install to the MBR, when I did it via the live cd i sudo'd grub, did root (hd0,0) and then setup (hd0).  I don't recall any option during the live cd grub installation attempt to install to the MBR.

---

### Post by jml on 2007-02-22
You may have to search Google, or a Windows Vista forum for this one.  I have read that Windows Vista treats the MBR differently than all previous versions of Windows.  That means that Grub is not able to repair itself as easily as it could with older versions of Windows.  Good Luck.  And post your experiences here when you can.

Joe

---

### Post by gozzerd on 2007-02-23
I don't have a copy of vista, so I can't verify anything, but i would be surprised if vista  put code into the mbr that would automatically  change  the info pointing to grub to point back to the vista boot location.
The mbr contains several things. One is the partition tables, which apparently were corrected. another is a pointer to the location where the pertinent boot info is. It sounds like the partiton tables were corrected, but the mbr code is still looking towards the windows partition for boot loader info. Most likely the windows partition has its active flag set and the ubuntu partition does not. You could try any of the disk tools to see. Parted, gparted, qtparted, fdisk, cfdisk, etc. I forget which is the best one to set it with. But if the ubuntu partition is set active, and the windows partition is not, and grub is re-installed to the mbr, and it still starts windows automatically, i would look at starman's pages, get a hex editor, and see if ms has done something sneaky.

---

### Post by betawind on 2007-02-24
Wellll, consider this problem fixed!  I started by taking the advice of gozzerd, booted up to my Ubuntu live cd and started with an fdisk -l.  I saw that both my linux drive and vista drive were flagged as boot.  I then opened up gparted and removed the boot flag from my vista partition, thinking it would let the linux drive boot.  When I restarted after that, my system went straight to a network boot (builtin mobo feature).  I then entered my bios to try and disable this feature to see if it would work or possibly give me another error to go off of.  When I entered my bios I found something I had been looking for previously, the order in which my hard drives were loaded.  It had my vista hard drive set to boot first, which meant the root issue was not with grub or the vista boot loader :p.  

Previous to doing all of this (since I had thought before this may have been the issue but was unable to find the bios setting for it), I had completely redone my IDE setup in the case to make my linux drive primart master (My setup in my case was all sorts of screwed up, I must have been high or something when I did it).  

Well, after fixing the hdd boot order in my bios I restarted.  Grub came right up.  I tried loading both ubuntu and vista, but neither worked.  I had forgotten that since I had changed my hard drive setup, I needed to redo where grub thought the operating systems were.  I booted back into my live CD, fixed up my menu.lst file, and now all is well.  Both OS's boot without a hitch, and I even have EXT3 read/write support in Vista.  I'm a very happy camper.

I guess the lesson to take away from all of this is if you're having problems w/ grub even recognizing, make sure your BIOS is set to boot off the correct hard drive first.  The funny thing with all of this is nothing was changed in my bios when I upgraded to Vista, and I had actually had to repair grub before when I installed XP.  Perhaps the vista bootloader is just *that* different from XP's.  

Oh well, thanks to both of you, and especially gozzard, without whom I would have never went the path I did to resolve this.  


~Brad

---


---
title: "big problem! portable WD and Local Disks."
date: 2008-05-04
forum: General Help
---

### Post by soundf on 2008-05-04
I've installed Ubuntu 8.04 desktop from CD(i wanted 2 install it from Windows but it said to me on start "File no Found" and things).
I had my WD portable 320gb connected to the computer while i installed Ubuntu and it installed the Ubuntu there, instead of the Local Disk(D) I cleaned up for it(219gb).
I want Windows and Ubuntu together(Chose on start) not only Ubuntu.
Now my WD320 have only 124gb, I can get it back at Windows Disk Menagement by deleting Ubuntu from there, though.

My question is that how do i install Ubuntu on (D) without getting my Windows deleted? because Ubuntu wants all of the hardisk and (C) is my Windows System.

Thanks.

---

### Post by ugm6hr on 2008-05-04
> **soundf said:**
> I want Windows and Ubuntu together(Chose on start) not only Ubuntu.
Now my WD320 have only 124gb, I can get it back at Windows Disk Menagement by deleting Ubuntu from there, though.

My question is that how do i install Ubuntu on (D) without getting my Windows deleted? because Ubuntu wants all of the hardisk and (C) is my Windows System.

You are looking to "dual-boot".

Do you have a Live CD or Alternate CD?  Which version of Windows, and which version of Ubuntu do you use?

Dual-booting is straightforward.  But installing is not something to be done unless you know what you are doing.

Make sure you back-up all important data before doing anything else.

---

### Post by soundf on 2008-05-04
I think its a LiveCD..

Download URL: [http://ubuntu.interhost.co.il/hardy/ubuntu-8.04-desktop-i386.iso](http://ubuntu.interhost.co.il/hardy/ubuntu-8.04-desktop-i386.iso)
Ubuntu Edition: Ubuntu 8.04 desktop
Computer Platform: i386

from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

I thought about it and iit would've been nice to have Ubuntu on my portable disk.

How much gb do i need to give it? I dont want to any short-on-memory problems on the future..

---

### Post by jojotjuh on 2008-05-04
> **soundf said:**
> I think its a LiveCD..

Download URL: [http://ubuntu.interhost.co.il/hardy/ubuntu-8.04-desktop-i386.iso](http://ubuntu.interhost.co.il/hardy/ubuntu-8.04-desktop-i386.iso)
Ubuntu Edition: Ubuntu 8.04 desktop
Computer Platform: i386

from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

I thought about it and iit would've been nice to have Ubuntu on my portable disk.

How much gb do i need to give it? I dont want to any short-on-memory problems on the future..

i know that swap needs to be around 2gb, and the operating system itself around 3-5 Gb, so i guess a minimal of 10GB, but that's a bit shallow if you want documents like movies and music. I have it at 40GB, and gave windows the rest (around 110 GB)

---

### Post by soundf on 2008-05-04
> **jojotjuh said:**
> i know that swap needs to be around 2gb, and the operating system itself around 3-5 Gb, so i guess a minimal of 10GB, but that's a bit shallow if you want documents like movies and music. I have it at 40GB, and gave windows the rest (around 110 GB)

i meant only for the operation because I think you can use the local disks for files and stuff..

---

### Post by ugm6hr on 2008-05-04
> **soundf said:**
> i meant only for the operation because I think you can use the local disks for files and stuff..

I would recommend 7-900MB for swap, with a further 7-9GB for Ubuntu.

/home (equivalent to My Documents) will be included in that - but you can save files elsewhere, as you said.

Be careful installing to USB drives, since GRUB (the booloader) defaults to hd0 (i.e. the first HD), so you may find that Windows will then refuse to boot unless you have your USB HD plugged in.

---

### Post by soundf on 2008-05-04
> **ugm6hr said:**
> 
Be careful installing to USB drives, since GRUB (the booloader) defaults to hd0 (i.e. the first HD), so you may find that Windows will then refuse to boot unless you have your USB HD plugged in.

you were right, how do i fix this?

---

### Post by ugm6hr on 2008-05-04
> **soundf said:**
> you were right, how do i fix this?

What version of Windows do you use?

Have you decided where you are going to install Ubuntu to?

---

### Post by soundf on 2008-05-04
> **ugm6hr said:**
> What version of Windows do you use?

Have you decided where you are going to install Ubuntu to?

I already did installed Ubuntu on my portable disk.
I have Windows XP 32bit

---

### Post by ugm6hr on 2008-05-04
OK. I've never done this myself, so let me explain what we are trying to do so you can research the potential solutions.

The final result I would suggest is something like this:
BIOS set to boot from USB as default.
GRUB bootloader on USB, with options of either Ubuntu or XP.
XP bootloader on internal HD, which will boot XP automatically.

This way, if you unplug the USB HD, XP will boot autommatically.
If plugged in, it will boot the GRUB menu.

First, restore XP as the default.  You need to restore the XP bootloader.  This is the easiest way to do this: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Then you need to install GRUB onto the HD.  Super GRUB disk is the easiest way to do this, although it can be done from the Ubuntu LiveCD (I think).  Try searching for restore GRUB, and just make sure you put it on the USB HD MBR (Master Boot Record).  Of course, given that you have only just installed Ubuntu, it may be quicker to just delete the Ubuntu partition, and reinstall with GRUB in the correct place.  The GRUB location is specified in the Advanced options when selecting the partitions in the "Manual" installation procedure.

---

### Post by soundf on 2008-05-05
The fix worked, but now I cant use Ubuntu because it boots only Windows.
After that, I've downloaded Uper GRUM from: [http://forjamari.linex.org/frs/?group_id=61&release_id=447](http://forjamari.linex.org/frs/?group_id=61&release_id=447)
and it still doesnt work.. and i dont want to delete Ubuntu from the portable disk

---

### Post by ugm6hr on 2008-05-05
> **soundf said:**
> The fix worked, but now I cant use Ubuntu because it boots only Windows.
After that, I've downloaded Uper GRUM from: [http://forjamari.linex.org/frs/?group_id=61&release_id=447](http://forjamari.linex.org/frs/?group_id=61&release_id=447)
and it still doesnt work.. and i dont want to delete Ubuntu from the portable disk

What happens when you boot the Super GRUB disk?

It should give you options to install GRUB.

---

### Post by soundf on 2008-05-05
nvm i fixed it.
tnx

---


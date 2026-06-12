---
title: "A question"
date: 2006-12-08
forum: General Help
---

### Post by hgmgtak on 2006-12-08
hi, everyone

I have a question on Xubuntu, 
which is "can xubuntu run on my old laptop computer smoothly"?

My old laptop computer's details as in follows.
CPU: P2 300MHZ
RAM: 96 MB SD RAM

Can Xubuntu run on my old laptop computer smoothly?

Thanks

---

### Post by az on 2006-12-08
> **hgmgtak said:**
> hi, everyone

I have a question on Xubuntu, 
which is "can xubuntu run on my old laptop computer smoothly"?

My old laptop computer's details as in follows.
CPU: P2 300MHZ
RAM: 96 MB SD RAM

Can Xubuntu run on my old laptop computer smoothly?

Thanks

It should.  However, you will need to use the alternate cd since you do not have enough ram to use the graphical (desktop) cd.

---

### Post by hgmgtak on 2006-12-08
> **azz said:**
> It should.  However, you will need to use the alternate cd since you do not have enough ram to use the graphical (desktop) cd.
thank you for your reply

Also, I have a question more

which is 

"How can I install Xubuntu in WinXP(the partition is Fat32)with my old laptop computer?"

thanks

---

### Post by hgmgtak on 2006-12-08
please help me
thanks

---

### Post by CatKiller on 2006-12-08
> **hgmgtak said:**
> "How can I install Xubuntu in WinXP(the partition is Fat32)with my old laptop computer?"

You don't. You would burn the .iso image to a cd (or otherwise get hold of a cd) and boot from it, so that the environment you install from is that provided by the installer.

(X)Ubuntu will not run from a FAT32 partition. FAT32 just isn't up to the task. The install process will let you re-partition the drive so that you can install it on a more sensible filesystem, like ext3. You'll have the option of either wiping the drive completely for (X)Ubuntu's use, or shrinking the existing partition and making a new one in the newly-freed space.

[These pages]("http://users.bigpond.net.au/hermanzone/") might help, although they were made for Ubuntu rather than Xubuntu.

---

### Post by hgmgtak on 2006-12-08
> **CatKiller said:**
> You don't. You would burn the .iso image to a cd (or otherwise get hold of a cd) and boot from it, so that the environment you install from is that provided by the installer.

(X)Ubuntu will not run from a FAT32 partition. FAT32 just isn't up to the task. The install process will let you re-partition the drive so that you can install it on a more sensible filesystem, like ext3. You'll have the option of either wiping the drive completely for (X)Ubuntu's use, or shrinking the existing partition and making a new one in the newly-freed space.

[These pages]("http://users.bigpond.net.au/hermanzone/") might help, although they were made for Ubuntu rather than Xubuntu.
thank you for your reply

My old laptop computer's cdrom is bad, which usually cant detect the cd =(

Are there any method that can install xubuntu without cdrom?

thanks

---

### Post by az on 2006-12-08
> **hgmgtak said:**
> 
"How can I install Xubuntu in WinXP(the partition is Fat32)with my old laptop computer?"


You cannot install Ubuntu in windows.  You can install Ubuntu alongside windows, if you want.  You chose which OS you want to use when you start up your computer.

You can also just install Ubuntu on top of windsows (erasing it).

Both ways are possible using the installer - you choose.

---

### Post by Biggus on 2006-12-08
Maybe you could remove the hard drive from the laptop to a machine which has a working CD-ROM, install Xubuntu, then switch the hard drive back?

I also noted that the system requirements include that you must have 1.5GB of free space ( [http://www.xubuntu.org/get]("http://www.xubuntu.org/get") ), does the laptop have that?

---

### Post by hgmgtak on 2006-12-08
> **azz said:**
> You cannot install Ubuntu in windows.  You can install Ubuntu alongside windows, if you want.  You chose which OS you want to use when you start up your computer.

You can also just install Ubuntu on top of windsows (erasing it).

Both ways are possible using the installer - you choose.
thank you for your reply =)

My old laptop's cdrom usually cant detect cd.
I afraid that my cdrom suddenly stop running while installing xubuntu...(after earsing winxp)

so...are there any method to install xubuntu without cdrom??

I would like to ask one more question. 
how many space will xubuntu occupied?

thank you

---

### Post by hgmgtak on 2006-12-08
> **Biggus said:**
> Maybe you could remove the hard drive from the laptop to a machine which has a working CD-ROM, install Xubuntu, then switch the hard drive back?

I also noted that the system requirements include that you must have 1.5GB of free space ( [http://www.xubuntu.org/get]("http://www.xubuntu.org/get") ), does the laptop have that?
Thank you for your reply.

My old laptop computer's harddisk has 4.0GB spaces..

I dont know how to remove the hard drive from the laptop...

---

### Post by hgmgtak on 2006-12-08
please help me

---

### Post by az on 2006-12-08
> **hgmgtak said:**
> My old laptop's cdrom usually cant detect cd.
I afraid that my cdrom suddenly stop running while installing xubuntu...(after earsing winxp)



What do you mean?  The bios is unable to boot from cd or that the optical drive is deffective?

If so, maybe it can be fixed.

There are tools that allow you to boot from a floppy and then chainload a cdrom.

---

### Post by hgmgtak on 2006-12-08
> **azz said:**
> What do you mean?  The bios is unable to boot from cd or that the optical drive is deffective?

If so, maybe it can be fixed.

There are tools that allow you to boot from a floppy and then chainload a cdrom.
Thank you for your reply.

I mean that my cdrom is usually not effective, which cant load the the cd properly.

---

### Post by az on 2006-12-08
> **hgmgtak said:**
> Thank you for your reply.

I mean that my cdrom is usually not effective, which cant load the the cd properly.

There is only a short list of things that can cause an optical drive to throw read errors intermittently.

If there is nothing obviously broken with it, you can try to dab the optical sensor with a tissue.  It is the little clear thing that usually has a sticker pointing to it which says "Do not clean with a tissue!"

You have nothing to lose and I have had success with this before.

If there is something obviously wrong with it (door does not close properly, makes a funny noise, etc) then maybe persue a different approach.

If there are BIOS settings for the device, try setting it to the most basic (slow) setting.  If you have a choice between DMA and PIO modes, chose one of the PIO modes.

---

### Post by hgmgtak on 2006-12-08
> **azz said:**
> There is only a short list of things that can cause an optical drive to throw read errors intermittently.

If there is nothing obviously broken with it, you can try to dab the optical sensor with a tissue.  It is the little clear thing that usually has a sticker pointing to it which says "Do not clean with a tissue!"

You have nothing to lose and I have had success with this before.

If there is something obviously wrong with it (door does not close properly, makes a funny noise, etc) then maybe persue a different approach.

If there are BIOS settings for the device, try setting it to the most basic (slow) setting.  If you have a choice between DMA and PIO modes, chose one of the PIO modes.
thank you very much =)

I have one more quiestion...

I have a mobile phone and there is a usb cable which can let the mobile phone and the computer connect together in windows.  Can Xubuntu do that?

Thanks

---

### Post by az on 2006-12-08
> **hgmgtak said:**
> thank you very much =)

I have one more quiestion...

I have a mobile phone and there is a usb cable which can let the mobile phone and the computer connect together in windows.  Can Xubuntu do that?

Thanks

What kinda phone?

---

### Post by hgmgtak on 2006-12-08
nokia

---

### Post by az on 2006-12-08
Maybe:

[http://packages.ubuntu.com/dapper/comm/obexftp](http://packages.ubuntu.com/dapper/comm/obexftp)

Maybe it's just like a usb hard drive, too.  I dunno.

---

### Post by hgmgtak on 2006-12-08
> **azz said:**
> Maybe:

[http://packages.ubuntu.com/dapper/comm/obexftp](http://packages.ubuntu.com/dapper/comm/obexftp)

Maybe it's just like a usb hard drive, too.  I dunno.
thank you

---

### Post by hgmgtak on 2006-12-26
> **azz said:**
> There is only a short list of things that can cause an optical drive to throw read errors intermittently.

If there is nothing obviously broken with it, you can try to dab the optical sensor with a tissue.  It is the little clear thing that usually has a sticker pointing to it which says "Do not clean with a tissue!"

You have nothing to lose and I have had success with this before.

If there is something obviously wrong with it (door does not close properly, makes a funny noise, etc) then maybe persue a different approach.

If there are BIOS settings for the device, try setting it to the most basic (slow) setting.  If you have a choice between DMA and PIO modes, chose one of the PIO modes.

I have tried that before.  It can't... =(
Is there any idea to install xubuntu without cdrom?

---

### Post by hgmgtak on 2006-12-26
does anyone have idea?

---

### Post by hgmgtak on 2007-01-26
Can I install xubuntu via ftp/http without cdrom?

---


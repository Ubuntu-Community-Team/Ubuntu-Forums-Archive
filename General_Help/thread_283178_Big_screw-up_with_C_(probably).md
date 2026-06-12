---
title: "Big screw-up with C: (probably)"
date: 2006-10-23
forum: General Help
---

### Post by BSAB_80 on 2006-10-23
Hi there, new here, but eager to learn more, and i'm in a bit of a pickle.
So this is what happened.

I got a new laptop, and did a clean install of Ubuntu (my first Linux foray!).
Loved the OS, definitively a fan and i'll keep it, but afterwards i thought i'd like a dual boot for the time being and decided on creating a new NTFS partition (which i thought was standard for Windows).

When i popped in the Windows XP (English) install, he told me that there was no HD and therefore he could not install.
Tried it with another Windows XP, now in Portuguese, and it installed with no problems, only he did it on the E: drive, not the usual C: label.
Found it odd, so i went back to the Gnome Partition Editor and deleted all partitions (the NTFS one and all the Linux ones), intent on making a fresh install of everything.

But it didn't work, Windows still says i have no HD, and i'm starting to get a bit freaked out (not a big computer head here, panic does ensue on occasion).
I know i can install Ubuntu fine, or even the Portuguese XP, but i can't help thinking i did something very wrong on Gparted.

Anyone can help me out and point me the error of my ways so i can correct them and become a better man?
(the other error besides wanting to keep Windows for a while more, obviously)

---

### Post by Paul41 on 2006-10-23
I have seen some people say that they Windows won't work unless it is installed first.  Ubuntu doesn't care if it is installed first or not.  I am not sure if this has anything to do with your problem or not.  Does anyone else know if this is true or not?

---

### Post by CatKiller on 2006-10-23
The only thing I can think of is that the English XP is an Upgrade disc and the Portuguese XP is a proper install disc. So the English one is looking for an existing XP install on the hard drive, that it can't find, so it complains.

---

### Post by CatKiller on 2006-10-23
> **Paul41 said:**
> I have seen some people say that they Windows won't work unless it is installed first.  Ubuntu doesn't care if it is installed first or not.  I am not sure if this has anything to do with your problem or not.  Does anyone else know if this is true or not?

I don't think that it's exactly true. Windows certainly used to only work if it was installed in the active Primary partition, but I don't believe that to be the case any more, and the Windows boot loader will insist on overwriting GRUB to make you only able to boot into Windows until you sorted it out again. It's all fixable though, and installing Windows first just gives you fewer things to fix.

The OP **will** have Windows installed first, should he choose to - he's already removed Ubuntu from the drive.

---

### Post by BSAB_80 on 2006-10-23
> **CatKiller said:**
> The only thing I can think of is that the English XP is an Upgrade disc and the Portuguese XP is a proper install disc. So the English one is looking for an existing XP install on the hard drive, that it can't find, so it complains.

Was looking at the discs just now, and the English one (two, actually, i tried another one to see if it was a faulty disc) are proper installs and the Portuguese one is a "Recovery DVD" they shipped with the laptop.
Is that any help?

It's just so puzzling, i've tried to even make the new partition a FAT32 one but still Windows says the HD isn't there.

---

### Post by Pelekophori on 2006-10-24
If your English version of XP is a bit old, it may need you to provide a separate driver for the hard disk before it can use it.  I used to have to do that with a previous computer whenever I installed Windows.  Windows wouldn't recognise the hard disk otherwise.    

At some stage in the setup process Windows asks you to press a key (F6 I think) to install 3rd party drivers.  If your laptop didn't come with one (because the provided recovery disk doesn't need it) then maybe the manufacturer's website might be able to help.

---

### Post by anaconda on 2006-10-24
> **Pelekophori said:**
> If your English version of XP is a bit old, it may need you to provide a separate driver for the hard disk before it can use it.  I used to have to do that with a previous computer whenever I installed Windows.  Windows wouldn't recognise the hard disk otherwise. 

This happens with older winXP install disks, IF you are trying to install windows to a SATA hard-drive. The orginal winXP doesn't regognize SATA disks....

---

### Post by BSAB_80 on 2006-10-24
> **Pelekophori said:**
> If your English version of XP is a bit old, it may need you to provide a separate driver for the hard disk before it can use it.  I used to have to do that with a previous computer whenever I installed Windows.  Windows wouldn't recognise the hard disk otherwise.    

At some stage in the setup process Windows asks you to press a key (F6 I think) to install 3rd party drivers.  If your laptop didn't come with one (because the provided recovery disk doesn't need it) then maybe the manufacturer's website might be able to help.

It's a Windows XP with SP2, isn't it recent enough?

---

### Post by Pelekophori on 2006-10-24
Bear in mind that needing the right driver is only a possible reason the English XP version may not recognise your laptop hard drive.  

Anaconda is right that my Windows XP was an old copy and that was why it didn't recognise SATA drives.  But I'm wondering if there's something odd about your laptop hard drive which requires a custom driver even a recent  generic Windows XP doesn't have.   The fact that the XP disk which came with the laptop recognises the drive suggests it's a possibility worth considering and eliminating.

---

### Post by Rhubarb on 2006-10-24
(isn't it lovely that Ubuntu installed fine, but windows is having install problems!)

---

### Post by BSAB_80 on 2006-10-24
> **Pelekophori said:**
> Bear in mind that needing the right driver is only a possible reason the English XP version may not recognise your laptop hard drive.  

Anaconda is right that my Windows XP was an old copy and that was why it didn't recognise SATA drives.  But I'm wondering if there's something odd about your laptop hard drive which requires a custom driver even a recent  generic Windows XP doesn't have.   The fact that the XP disk which came with the laptop recognises the drive suggests it's a possibility worth considering and eliminating.

It's a Fujitsu-Siemens Amilo P1505, btw.

I'll look into it, thanks for all the help so far, guys!

---

### Post by BSAB_80 on 2006-10-24
> **Rhubarb said:**
> (isn't it lovely that Ubuntu installed fine, but windows is having install problems!)


I loved that too, should be a sign of something, eh?

---

### Post by BSAB_80 on 2006-10-24
You know what, screw Windows, i'll just go with Ubuntu for good.

One question, is there a way to update Ubuntu offline, or download Automatix and then run it when not connected to the internet?

---


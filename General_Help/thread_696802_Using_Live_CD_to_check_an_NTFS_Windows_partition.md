---
title: "Using Live CD to check an NTFS Windows partition?"
date: 2008-02-14
forum: General Help
---

### Post by mjpatey on 2008-02-14
Hi,

My wife, who isn't very familiar with Ubuntu, is at work trying to help a colleague rescue her Windows laptop.  She's done this before with a DOS boot disk, and may be able to find such a disk at some point, but right now all she has access to is a Gutsy Live CD.

Can she boot to the Gutsy Live CD and instantly have access to the NTFS volume?

She was hoping to run chkdisk under DOS to check for errors, and then attempt to copy the contents of the drive to an external USB drive as a backup.

My main questions are:  Does she have to mount the NTFS volume herself, or will it automatically come up in /media/sda1 or /media/hda1?  And, can she safely run fsck on the Windows volume by simply typing the following:

```
fsck /media/hda1
```

Thanks for any ideas you may have!

-Mark

---

### Post by pietjanjaap on 2008-02-14
Boot from windows cd, then push R, then go to recovery console (like dos,but isn't), then do chkdsk on the disk.

Ubuntu go to applications, systemtools,ntfs configuration tool, check it, and read the ntfs disk.

---

### Post by mjpatey on 2008-02-14
I'll let her know that, and hope she can find a Win install disc.  If she can't find one, I just did a bit of research that has led to another question...

I just booted from a Gutsy Live CD myself (and am writing this from within that live session), and noticed when fully booted into Gnome, all disks simply appear in the window when I go to Places-->Computer.  This is awesome!!!

But... they only appear in /media AFTER I've accessed them in Nautilus, as if accessing them in Nautilus causes the system to mount them, but before that, they're not mounted.  When I opened a Terminal initially, and typed "cd /media", all I saw was my external USB hard drive.  No hda1, sda1, etc.

So... if my wife isn't lucky enough to get the full GUI experience when she boots her Live CD on her colleague's very old laptop, will she be stuck with unmounted drives that she needs to mount manually before she can access them?  I just don't want her to be stuck at this person's house and hit a dead end.

Thanks again for any light you can shed!

-Mark

---


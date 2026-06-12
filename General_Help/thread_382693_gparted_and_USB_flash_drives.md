---
title: "gparted and USB flash drives"
date: 2007-03-12
forum: General Help
---

### Post by stchman on 2007-03-12
Hello all, I am wondering if there is some secret to using gparted with USB flash drives.  I recently had a 256MB USB flash drive that I was playing around with and I could not get gparted to format it in any file system.  I had to go to an XP machine and then format it in FAT32.  Does gparted have problems with USB flash drives?  I have an external USB HD that is currently in NTFS that I want to format in FAT32 (both windows and linux can read/write FAT32).  will gparted handle this?

Thanks

---

### Post by laidback on 2007-03-12
Ref USB HD, yes Gparted will do this. Remember the drive cannot be mounted whilst you repartition. I have a 250Gb USB hdd and use Gparted to create/adjust the partitions. It has ntfs and Linux partitions, I use ext3 but it could just as easily be Fat32 which is an optional format.

Ref Flash. Have you unmouted it before attempting a reformat?

---

### Post by laidback on 2007-03-12
I've just tried to reformat my Flash stick, Gparted doesn't seem to like it, anyone know why?

It starts off OK but errors when you Activate the job.

---

### Post by stchman on 2007-03-12
> **laidback said:**
> Ref USB HD, yes Gparted will do this. Remember the drive cannot be mounted whilst you repartition. I have a 250Gb USB hdd and use Gparted to create/adjust the partitions. It has ntfs and Linux partitions, I use ext3 but it could just as easily be Fat32 which is an optional format.

Ref Flash. Have you unmouted it before attempting a reformat?

Yes, you must unmount the USB flash drive or gparted GUI has the format option greyed out. When I select new and the file system (fat) I then apply and gparted gives me errors.

---

### Post by stchman on 2007-03-12
> **laidback said:**
> I've just tried to reformat my Flash stick, Gparted doesn't seem to like it, anyone know why?

It starts off OK but errors when you Activate the job.

I get the same thing.  I wonder if it is all USB storage devices or just flash drives.  I have an old USB HD that I want to reformat.

---

### Post by laidback on 2007-03-12
Well get this, I have a copy of the Live CD version of Gparted so I loaded that up and had a go at reformatting my flash drive, NO PROBLEM, straight to it, it's now FAT32.


What did I do...
Put Flash drive in a usb socked
booted my Gparted Live CD...it found flash drive (250Mb)
selected it in both top right corner and within the body of the screen
pressed delete ( to delete existing partition)
selected the greyed out area again
specified a format with 1 partition, i.e. whole stick
(noted the instructions in the window at bottom of screen, is it what I want?, yes so..)
press Apply

Off it went...no issues at all.


Rebooted my Ubuntu system...leaving flash drive in USB
Opened USBdisk when icon appeared after boot up....empty disc
Copied 2 files to disk
Opened files from Flash disc....OK
Ejected flash drive and removed from pc
reinserted flash drive..opened files...all OK

I reckon it works.

Maybe there's a slight problem with the Gparted in Ubuntu.
Could it be a premission/rights issue..although you give pswd to access Gparted in the first place..odd

---

### Post by laidback on 2007-03-12
Ref USB hdd's. I have a 250Gb USB hdd and use Gparted to partition/format the drive. But I do tend to use my Gparted Live CD to do the job, cannot be certain on whether I've always used it.

I've recommended Gparted to other Ubuntu users and they report success. (hdd use)

---

### Post by laidback on 2007-03-14
It might be significant that the default Ubuntu version of Gparted is 0.1, but the latest version on the Gparted web site is 0.3.3. This is the version I use with my Live CD, it does seem to be more robust.

---


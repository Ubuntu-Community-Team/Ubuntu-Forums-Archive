---
title: "Ubuntu not starting, I do not know how and why it happened"
date: 2018-12-30
forum: General Help
---

### Post by saleb on 2018-12-30
So, everything worked fine, power, restart, and everything I see is Grub 2.02 terminal prompt. 
After a short search through the web I found that I should point it to boot drive and boot folder or linux image. (hd1,gpt1) has folder /efi, but there is no folder boot, linux, and similar.
Booted ubuntu live on usb, when clicking the /dev/sdb2 in nautilus named "500 gb volume" it says "Unable to access location. Error mounting /dev/sdb2 at /media/ubuntu/[some long hex number, 8-4-4-12 characters]: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error"

That 500gb drive is the ssd which ubuntu reformated and installed itself to 10 days ago, so it's not an ntfs partition

What should I do now?

Edit:
Using the disks utility I found that the 500gb disk has 537mb fat partition, 500gb ext4 partition and 1.1mb free space. So, how do I access it and how do I repair what ever happened?
Check disk inside the same utility says fat partition ok, ext4 partition, error while checking partition: "exit code 12:e2fsck 1.44.1; e2fsck: the journal superblock is corrupt while checking jornal for /dev/sdb2; e2fsck: cannot proceed with file system check (udisk-error-quark, 0)"

---

### Post by vidtek on 2018-12-30
> **saleb said:**
> So, everything worked fine, power, restart, and everything I see is Grub 2.02 terminal prompt. 
After a short search through the web I found that I should point it to boot drive and boot folder or linux image. (hd1,gpt1) has folder /efi, but there is no folder boot, linux, and similar.
Booted ubuntu live on usb, when clicking the /dev/sdb2 in nautilus named "500 gb volume" it says "Unable to access location. Error mounting /dev/sdb2 at /media/ubuntu/[some long hex number, 8-4-4-12 characters]: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error"

That 500gb drive is the ssd which ubuntu reformated and installed itself to 10 days ago, so it's not an ntfs partition

What should I do now?

Edit:
Using the disks utility I found that the 500gb disk has 537mb fat partition, 500gb ext4 partition and 1.1mb free space. So, how do I access it and how do I repair what ever happened?
Check disk inside the same utility says fat partition ok, ext4 partition, error while checking partition: "exit code 12:e2fsck 1.44.1; e2fsck: the journal superblock is corrupt while checking jornal for /dev/sdb2; e2fsck: cannot proceed with file system check (udisk-error-quark, 0)"

Saleb-

Sounds to me like a dodgy ssd.  If you only installed 10 days ago, you probably won't mind doing a re-install.  

Ssd's when they start to fail write blocks to other parts of the internal memory map, and mark the dodgy ones as bad.  If you completely filled the drive, as a normal install would, it only leaves a megabyte or so at the very end.

I suggest you do a complete install again, this time ***manually*** partitioning the ssd yourself (Ubuntu has a choice for doing this in the partitioning installation options), leaving a gigabyte or so at the end of the drive un-formatted.

The way I do it is to partition like this (assuming your drive is /dev/sdb as in your post):

1) partition /dev/sdb1 is a boot partition, it is usually labelled EFI or SYSTEM, I always make mine greater than the 100mb default, usually about 250mb.  If you install multiple operating systems, the standard 100mb is quickly used up and it causes all sorts of boot problems.

2) /dev/sdb2 is my operating system designated root /  I usually allow at least 70gb for this to allow for updates, temp. files growing /var directory etc.

3) /dev/sdb3 for my home partition, I usually make it as large as possible, at least 100gb.

I then leave at least one gb at the end un-formatted to allow for drive errors to be catered for.  (sorry about the bad English, I don't normally end sentences with prepositions, but I'm knackered at the mo....):cool:

Tony

---

### Post by saleb on 2018-12-30
Thanks, Tony

I'll try to set it up manually. It is a huge help that you wrote the sizes of individual partitions that is applicable now. Most of the recommendations that I have found on the web are 10 or more years old with much lower values. 

About the SSD I came to the same conclusion because the windows that was there until 10 days ago, went in the same way, reset at one moment and boot sector irreparably damaged in the next moment. Its to coincidental that it happens twice in less then a month with two different partition types.

---


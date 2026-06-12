---
title: "Using gnome disk utility to save image of windows drive?"
date: 2014-04-21
forum: General Help
---

### Post by nuttzo31 on 2014-04-21
I have windows on one hard drive and ubuntu on the other and as far as i can tell if  i make a system image of the entire windows  drive which includes uefi,recovery partition etc and i then later i need to reimage i can just put in a livecd,boot up and restore image as long as the image is to the same drive or one at least of equal size?  I assume gnome disk just does a dd if=/dev/sda etc to make a byte by byte copy of entire hdd.  If my assumptions are correct then do i not need to worry about clonezilla if all i need is an image or does clonezilla have other benefits?

---

### Post by Mark Phelps on 2014-04-21
Personally, I have found that Windows utilities do a better job of imaging Windows filesystems, Linux utilities, of Linux filesystems.

If I were you, I would use Macrium Reflect (MR) to do the Windows image backup.  You can download and install the free version in Windows.  You should also use the option to create and burn a Linux Boot CD.  That will allow you to boot from the CD to do an image restore using MR.

---

### Post by rbmorse on 2014-04-21
I second Mark's recommendation.  BTW, Macrium Reflect does a bang up job of imaging Linux partitions, too.  You have to boot from the Reflect rescue boot medium to create the images because Linux won't let you image mounted partitions.  Reflect now works with GPT disks, too.

---


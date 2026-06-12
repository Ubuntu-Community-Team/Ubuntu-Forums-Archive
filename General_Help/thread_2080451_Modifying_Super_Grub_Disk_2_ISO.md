---
title: "Modifying Super Grub Disk 2 ISO"
date: 2012-11-04
forum: General Help
---

### Post by MYz160 on 2012-11-04
Just a little background:  I want to be able to boot .iso files on a usb using the loopback feature from grub2.  So far I've been able to do this by manually installing grub, then adding the relevant menuentries for grub.cfg on a usb.

But I wanted to try Super Grub Disk 2 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/). I downloaded it and it apparently has an .iso autodetect feature.  So I open the .iso with ISO Master, and shove in ubuntu 12.10 (both the 32 and 64 bit versions)  into the boot/boot-isos/ directory.  I go ahead and save it as a new .iso file, and sudo dd it onto the usb.

But it turns out it is unbootable.  On further examination when I try "sudo dd if=newiso.iso bs=512 count=1 | hexdump -C -v" to see what the first sector looks like, it is empty! The only nonzero bytes are way into the iso and is littered with 'Made by ISO Master' etc... By using ISO Master to insert some ubuntu livecd .isos it took out the whole first sector

I even try to use mount as iso9660 on the original .iso, but it only mounts it as a read only filesystem.  

The funny thing is, feeding it to Oracle Virtualbox works just fine. Is there a proper way to put these ubuntu .iso files into the super grub disk 2 .iso?

---


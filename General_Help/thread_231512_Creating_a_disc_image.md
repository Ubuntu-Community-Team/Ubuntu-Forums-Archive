---
title: "Creating a disc image"
date: 2006-08-07
forum: General Help
---

### Post by kernco on 2006-08-07
I have found online sources that say the way to make an iso image from a CD is to run "dd if=/media/cdrom of=image.iso".  When I do this, the output is:
dd: reading `/media/cdrom': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000113 seconds, 0.0 kB/s

Why doesn't this work?

---

### Post by bensexson on 2006-08-07
Unfortunately I do not know why dd is not working.  I personally use mkisofs.  look at the man file for mkisofs.

---

### Post by PatrickMay16 on 2006-08-07
> **kernco said:**
> I have found online sources that say the way to make an iso image from a CD is to run "dd if=/media/cdrom of=image.iso".  When I do this, the output is:
dd: reading `/media/cdrom': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000113 seconds, 0.0 kB/s

Why doesn't this work?

Hello!
I tell you, it's not working here because you're specifying the mount point for the cdrom rather than the device file.
Instead, it should be something like this:
dd if=/dev/cdrom of=cdromimage

If you have more than one CD drive or hard disk, to find out the device file for your cdrom, use this command and see what it says:

eject -v

It will eject your cdrom drives and give some info. Here's what it says for my machine:
> 
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hdb'
eject: `/dev/hdb' is not mounted
eject: `/dev/hdb' is not a mount point
eject: `/dev/hdb' is a multipartition device
eject: trying to eject `/dev/hdb' using CD-ROM eject command
eject: CD-ROM eject command succeeded


Most likely, /dev/cdrom will do fine.

Good luck!

---

### Post by PatrickMay16 on 2006-08-07
Oh, by the way, you might want to try out Gnomebaker. It can make ISO images of CDs.
Fackin' like a master.

---

### Post by lindylex on 2008-06-14
PatrickMay16, perfect, simply, right to the point answer, thanks works for me.

Using Debian Etch 4.0

---


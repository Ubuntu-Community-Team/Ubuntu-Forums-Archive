---
title: "USB flash drive no longer working"
date: 2007-09-17
forum: General Help
---

### Post by viergeame on 2007-09-17
I have a USB flash drive that I have been using for quite awhile, and I wanted to put Damn Small Linux on it.  I tried to use one of the guides on their site and now my drive doesn't work.  I was trying to edit the filesystem using fdisk and I got an error saying that the changes couldn't be written.  Now when I plug the drive in the system recognizes it, but I can't access it.  I tried using it on my other computer to make sure it wasn't just a problem with my USB ports but it won't work on there either.  I really need to be able to use the drive, but I am lost on what to do with it.

---

### Post by HermanAB on 2007-09-17
There is a utility by Hewlett Packard that can be used to reformat USB flash drives.  After some Googling, It think it could be one of these:
[http://www.pcworld.com/downloads/file/fid,64963-order,1-page,1-c,peripherals/description.html](http://www.pcworld.com/downloads/file/fid,64963-order,1-page,1-c,peripherals/description.html)
[http://h18007.www1.hp.com/support/files/server/us/download/24828.html?jumpid=reg_R1002_USEN](http://h18007.www1.hp.com/support/files/server/us/download/24828.html?jumpid=reg_R1002_USEN)

Of course, you need a Windoze machine to run it, but it the simplest way to fix a USB device that I know of.

Otherwise, try the Linux 'mkfs.vfat' to reformat it.

Cheers,

Herman

---

### Post by viergeame on 2007-09-17
I'll try mkfs.vfat.  Hopefully that works, as I don't even have access to a Windows machine anymore since I got my whole family to switch to Linux.  Or maybe it will run in wine.

---


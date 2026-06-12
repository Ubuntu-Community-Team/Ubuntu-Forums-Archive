---
title: "Trashed file on USB Flash Drive"
date: 2007-12-19
forum: General Help
---

### Post by teachop on 2007-12-19
Here is what led to a trashed USB stick directory:

I created an .xls on my Mac, and copied it to my MSDOS formatted USB stick.  I put the stick in my Ubuntu (up to date) laptop, and opened the file directly on the USB stick, it used OpenOffice.  I made lots of changes to the file, and then saved back to the USB stick (in .xls format).

I right clicked on the USB and picked unmount, and put it in my Mac later.  The Mac could no longer open the file.  The laptop with linux could no longer open the file.  I put it in a Windows laptop, repaired the drive, and ended up with one of those .000 files.  I renamed the file .xls and it is fine except for the last few changes I made are missing.

What happened I don't know.  The Ubuntu laptop (Acer Aspire 3100) with OpenOffice seems to have trashed the USB stick, and Windows was able to recover it.  There are a lot of steps in that chain, does anybody know what went wrong, or how to avoid it?

---

### Post by TheLions on 2007-12-19
had you unmounted drive before removing usb?

---

### Post by danwood76 on 2007-12-19
It sounds like openoffice still had the file open when you removed the flash drive.
Make sure you close files down and it properly unmounts the drive before removing.

The alternative is to make sure you dont open files straight from a fat formatted USB pen drive. The FAT filesystem is very poor and unstable, its best to use a journaling filesystem. If you need it to be compatible with mac, windows and linux I would look into installing ntfs-3g on your mac, there are OSX packages on the ntfs-3g site. and using the ntfs filesystem as it will have better data integrity.

---

### Post by teachop on 2007-12-19
I closed OpenOffice and right clicked on the USB drive icon, and selected unmount before pulling the drive.

Unfortunately I have embedded systems that only understand FAT16, so I am kinda stuck in the MSDOS format even if it does stink.  Either that or get another stick, they are sure cheap now!

It seems best to copy from the USB to the hard drive in linux, and work on the file there.  When I am done I will copy it back to the stick.  But I would like to narrow down what went wrong at some point.

Thanks.

---


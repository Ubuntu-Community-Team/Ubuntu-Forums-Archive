---
title: "help with formatting Floppy disks"
date: 2017-12-13
forum: General Help
---

### Post by roadrash on 2017-12-13
I know this has probably been asks many times and I have read many earlier posts all of which gave me errors.  Ive been using Ubuntu for way over 15 years buty never yet managed to format a floppy successfully and end up giving up.

I am curently doing a lot of work on various types of floppy, both 1.44mb and 720k.
Its all a bit confusing that it seems floppies need low level formatting before formatting with a file system. This sounds like the old days of prepping a MFM/RLL hard drive with Debug G=C800:5 like back in the 1980's
I cant believe its that complex to format a floppy disk in modern Linux.  I did find a very nice KDE app called Kfloppy which has a graphical interface and looks ideal but that too is giving errors when I run it, the last error I got and couldn't resolve was "Full formatting of a user given device is not possible" does anyone know how to cure this? or please help me format floppies easily using the Terminal as its annoying having to keep rebooting into windows just to format a floppy.  many thanks

---

### Post by Dennis N on 2017-12-13
> Its all a bit confusing that it seems floppies need low level formatting before formatting with a file system.

There is a utility named **ufiformat** for the low level formatting of floppy disk. It requires an external USB floppy drive (cost around $10-20). 

The program is still available here for download:

[http://www.geocities.jp/tedi_world/format_usbfdd_e.html](http://www.geocities.jp/tedi_world/format_usbfdd_e.html)

It works. I used it in the past.

---


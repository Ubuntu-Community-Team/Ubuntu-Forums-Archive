---
title: "usb-usb large file transfer quits at 4Gb"
date: 2008-01-20
forum: General Help
---

### Post by miatawnt2b on 2008-01-20
I am trying to transfer a bunch of DVD iso files (about 4.4Gb each) between two USB drives.  The drives both are formatted FAT32 for Windows operability. 

After starting the transfer, the first file stops at 4Gb (the orig is 4.4Gb) and then the transfer just quits.  When this happens, all of the windows on the desktop and the icons disappear for a few seconds before returning.  The drives don't seem to actually disconnect as there is nothing in the syslogs.

What is happening?

-J

---

### Post by gsiliceo on 2008-01-20
Its a limitation of the fat32 filesystem, it doesnt work with files larger than 4 gigs, not even windows can.
You need to split the files or format your drive with ext or ntfs.

---


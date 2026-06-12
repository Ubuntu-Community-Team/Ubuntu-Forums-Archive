---
title: "Hard drive install can't read rescue floppy"
date: 2008-07-07
forum: General Help
---

### Post by Spaceman9 on 2008-07-07
I used StartUp-Manager to create a rescue floppy. My hard drive install of Ubuntu 8.04 LTS can't mount and read the files on the floppy but Nautilus on the Ubuntu Live CD can. My hard drive install of Ubuntu can mount and read all my other floppies though from my internal floppy drive and my USB floppy drive.

Is there anything I can do to get my installed Ubuntu to mount and read the rescue floppy? Thankx for any help.

This is fstab from my hard drive install of Ubuntu.

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=00186574-55f8-44d1-ac03-04b9ebb7cc9a /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda5

UUID=cb772597-a441-4caf-a123-8c8fe300956c /home           ext3    relatime        0       2

# /dev/sda6

UUID=4db8a804-f90a-4ac6-a93d-51ed119ee827 none            swap    sw              0       0

# /dev/sdb5

UUID=8070c047-730f-4378-ae5a-869eb51318f6 none            swap    sw              0       0

# /dev/sdc5

UUID=4766e575-f47c-454d-8d8e-7bae96ff910b none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,users,noauto,fmask=111,dmask=000,exec,utf8 0       0

/dev/sdd        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by plucky on 2008-07-07
> Is there anything I can do to get my installed Ubuntu to mount and read the rescue floppy? 

Open a terminal and ```
sudo mount /dev/fd0 /media/floppy0
```

and the floppy icon should appear on your desktop.

Don't forget to un-mount it before removing the floppy.

Good Luck

---

### Post by Spaceman9 on 2008-07-07
Thankx Plucky. I typed sudo mount /dev/fd0 /media/floppy0 and was asked for my password. I didn't get an icon on my desktop but I did get an icon in  Nautilus and Nautilus can see the files on the floppy now. I can unmount it in Nautilus. 

What does it mean that I didn't get an icon on my desktop? Do I have something set up wrong in Ubuntu?

---

### Post by plucky on 2008-07-07
> What does it mean that I didn't get an icon on my desktop? Do I have something set up wrong in Ubuntu? 



Not really sure but my fstab has ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```for the floppy.

Also the behavior for partitions changed in Hardy for mounted partitions and I think there is a setting somewhere to allow mounted drives to show up on the desktop,not sure where.


Good Luck

---

### Post by Spaceman9 on 2008-07-07
> **plucky said:**
> Not really sure but my fstab has ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```for the floppy.

Also the behavior for partitions changed in Hardy for mounted partitions and I think there is a setting somewhere to allow mounted drives to show up on the desktop,not sure where.


Good Luck

I added the fmask=111,dmask=000, because I read this page [https://help.ubuntu.com/community/MakeFloppyDriveAvailableToEveryone](https://help.ubuntu.com/community/MakeFloppyDriveAvailableToEveryone) and I thought it might help Ubuntu mount and read the rescue floppy.
 
/dev/fd0 /media/floppy0 auto rw,users,noauto,fmask=111,dmask=000,exec,utf8 0 0

/dev/sdd /media/floppy1 auto rw,user,noauto,exec,utf8 0 0 

It didn't help though so I didn't add it to my USB floppy. What you told me to type in worked though.

This page [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy) says a boot floppy is formated with the ext2 filesystem. I don't know if that's what StartUp-Manager uses but I'd have to believe it is.

I'll search and see what else I can find out. Thankx for the help.

---


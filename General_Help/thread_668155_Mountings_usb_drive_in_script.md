---
title: "Mountings usb drive in script"
date: 2008-01-15
forum: General Help
---

### Post by pancakedan on 2008-01-15
Hi,

I am trying to run a script to backup my server then mount my usb drive (formatted ext3) on the server, move the backup to the usb drive then unmount the drive.

The script keeps failing at the point of mounting the drive.  Here is what I am using to mount the drive:

mount -t ext3 /dev/sda1 /usb

and the error:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I am able to mount the drive ok when just using the above command when not in a script.

Thanks

---


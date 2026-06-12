---
title: "can't mount floppy"
date: 2007-06-10
forum: General Help
---

### Post by dominator22 on 2007-06-10
I just installed a floppy drive so I could play an old dos game I found, but I can't mount the disk.  mount takes a very long time, then exits without error and the floppy is not mounted. 

The cables are properly connected.  BIOS detected the drive correctly.  My fstab entry is like so: 

/dev/fd0 /mnt/fd auto rw,noexec,users,auto,sync 0 0

Thanks for your help.

EDIT: I'm mounting the floppy like so: mount -t vfat /dev/fd0 /mnt/fd
/mnt/fd is owned by root:plugdev with rwxrwx-- permissions

---

### Post by Mr. C. on 2007-06-10
Floppies go bad and will fail to mount, or will have read/write errors leading to timeouts. Have you verified that the floppy is mountable on a Windows PC ?

MrC

---

### Post by Butthead on 2007-06-10
I access my floppy drive (after mounting like you do) by opening up the desktop and hitting the "up" arrow key found in there (not the one on the keyboard though!) until I see the "media" folder listed.  Then double clicking the fd0 in there brings up the floppy disk contents in a konqueror window.

I know, confusing. :confused:

---


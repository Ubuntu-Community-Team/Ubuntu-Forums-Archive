---
title: "Can't mount cd even an audio cd is automatically played"
date: 2007-12-10
forum: General Help
---

### Post by Ashrentum on 2007-12-10
I explain. I put a music cd or any other multimedia cd, and it is automatically played or I see a list of programs to open with. The problem is that /media/cdrom is completely empty and there is no other mount point for the cd.

This is my fstab for the cdrom:
**/dev/hda        /media/cdrom0   udf,iso9660     group,auto,exec          0       0**

**I can't mount it** manually:

mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The funny funny thing is that If I put a data cd, for example the ubuntu cd, I can mount it! ?????

I run it being root, the type is iso9660 and /dev/hda must be ok. 

I have no clue what is happening. Before I used debian using /dev/hda as well and everything worked perfectly

My sistem:
(x)ubuntu 7.10, original kernel
laptop Fujitsu Siemens Amilo Pa 1510

---

### Post by logos34 on 2007-12-10
you should have a folder **cdrom0** in /media.../media/cdrom should be empty because it's usually just a symlink pointing to cdrom0 or cdrom1...

create the folder if you don't:

sudo mkdir /media/cdrom0

'noauto' is the default option for cdrom line in fstab, so maybe try that instead.  You can then control whether the cd mounts or not in system>prefs>removable drives>storage tab>mount removable media

---

### Post by Ashrentum on 2007-12-10
I know cdrom is a symlink. In fact in fstab is written cdrom0, and I it works with data cd, the real directory and the link... I had auto before, by default, and it is the same.

I suppose there is a little bug there. Maybe the system mount it in a way, but without put it in the mtab mount list, and try to mount gives error because is in fact already mounted.......

No clue

---

### Post by logos34 on 2007-12-10
> **Ashrentum said:**
>  Maybe the system mount it in a way, but without put it in the mtab mount list, and try to mount gives error because is in fact already mounted.......

that's why I said try it with noauto.  but it's probably some other issue.  It always seems to be something else...

---

### Post by eggdeng on 2007-12-10
> The problem is that /media/cdrom is completely empty and there is no other mount point for the cd.
This is as it should be -  audio CDs are not mountable. Why would you want to mount one anyway?

---

### Post by logos34 on 2007-12-10
I thought the problem was that Ashrentum couldn't **manually** mount **data** cds.

---


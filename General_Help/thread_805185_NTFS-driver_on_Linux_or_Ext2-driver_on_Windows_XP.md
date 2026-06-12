---
title: "NTFS-driver on Linux or Ext2-driver on Windows XP?"
date: 2008-05-23
forum: General Help
---

### Post by yes9111 on 2008-05-23
For a shared partition between Windows XP and Linux (dualboot), would it be better to use the ntfs driver for Linux or use a Ext2 driver for windows XP?

---

### Post by tamoneya on 2008-05-23
ntfs drivers are already installed in ubuntu and they are part of the ntfs-3g package if you want to install them manually.You mount a drive like this```
sudo mount -t ntfs /dev/sda1 /windows
```
As for ext2/3 in window I use fs-driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by yes9111 on 2008-05-24
I know how to do both.  I just want to know which method is more stable; either have a NTFS shared partition with the ntfs-3g driver loaded or have an Ext2 partition with the ext2 driver for windows.  

I'm asking this because I remember someone saying that the NTFS support on GNU/Linux is better/stabler.  
BTW, I need to be able to write onto the files...

---

### Post by sune_cph on 2008-05-24
I've used the Ext2 driver on Windows (XP and Server 2003) for a long time and never had any issues, so I can highly recommend that one.

/Sune

---

### Post by tamoneya on 2008-05-24
i would say fs-driver is more stable however it is a pretty close call at this point.  The main reason is because ext2 and ext3 are open as oppsed to ntfs which is closed abnd had to be reverse engineered and therefore it is more prone to errors due to oddities added by microsoft.

---

### Post by PmDematagoda on 2008-05-24
> **tamoneya said:**
> i would say fs-driver is more stable however it is a pretty close call at this point.  The main reason is because ext2 and ext3 are open as oppsed to ntfs which is closed abnd had to be reverse engineered and therefore it is more prone to errors due to oddities added by microsoft.

Not necessarily, in my case I actually found ntfs-3g to be more reliable than ext2fs did, in the case of ext2fs it actually caused some trouble since the file system was improperly handled and caused checks during boot-up almost all the time.

I would recommend the ntfs-3g approach.

---

### Post by pietjanjaap on 2008-05-24
I would not let windows on my ubuntu files, security.

---

### Post by shae on 2008-05-24
I would vote for a third choice if you do not plan on using particularly large files on the shared drive.  What about Fat32?  It has great Linux and Windows support.

---

### Post by barnex on 2008-05-24
I'm using ntfs-3g under linux for quite a while without problems, so I think you can really trust it.

---


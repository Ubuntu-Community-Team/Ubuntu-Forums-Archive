---
title: "Persistence usb mounted but ..."
date: 2015-08-15
forum: General Help
---

### Post by dsx2 on 2015-08-15
When i boot Linux with live Usb persistence the storage is available in 

  ```
[INDENT]   /lib/live/mount/persistence/sdbx

 [/INDENT]

```
 But I can't find the device storage volume in the desktop or in the nautilus device side  as other available partition.

  Any idea how to solve this  ?

---

### Post by dsx2 on 2015-08-16
Is the question clear or need some clarification ?

---

### Post by yancek on 2015-08-16
It's not clear to me.  Since you are posting on an Ubuntu forum, can we safely assume you are using Ubuntu?  If not one of it's derivatives, if so which one and which release, 14.04 or later?

How did you create the bootable flash drive, what software did you use?  It does boot successfully, correct?  Is the problem that you can't save files?  Some other problem?  If you can boot it, do you see partitions when you run this command from a terminal:  sudo fdisk -l(Lower Case Letter L in the command).  You might post that output here.

Did you create a persistent file or partition?
If the persistence is created correctly, you should be able to save file/folders which are still there on reboot similar to an actual install.

---


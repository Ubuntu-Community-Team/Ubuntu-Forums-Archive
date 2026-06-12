---
title: "Mount Point Setting Error"
date: 2008-04-27
forum: General Help
---

### Post by harusp3x on 2008-04-27
I accidentally made a mistake in applying a mount point to a drive and now I am unable to mount it. How do I clear these mount options?

_Thank you.

---

### Post by Oldsoldier2003 on 2008-04-27
> **harusp3x said:**
> I accidentally made a mistake in applying a mount point to a drive and now I am unable to mount it. How do I clear these mount options?

_Thank you.

edit /etc/fstab and correct the options then ```
sudo mount -a
```to mount the device

---

### Post by harusp3x on 2008-04-27
I can't find the entry to the drive in it. I only see entries for the current filesystem, the swap, and my optical drives. I'm looking for sda1 I believe, but it isn't there.

---

### Post by Oldsoldier2003 on 2008-04-28
```
sudo fdsk -l
``` from there you should be able to identify your partition so you can make a proper fstab entry

---

### Post by harusp3x on 2008-04-29
Ok, apparently the partition I'm looking to mount is sdb1, but I don't know what to set for the mount point in fstab.

---

### Post by fbianconi on 2008-09-06
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

shows the bug, and the solution:

open gconf2, and change the key /system/storage/volumes/_org_freedesktop_Hal_devices_voume_uuid_*/mount_point

to some non-directory value (like "disk" not "/media/disk")

note the asterisk to expand your partition uuid.
actually I have it in /system/storage/drives

---

### Post by QwUo173Hy on 2009-03-17
Another (and maybe easier option) is to mount it from the terminal to a temporary folder.

> mkdir tmp
sudo mount /dev/<drive> /home/<user>/tmp

Now you can right click on the drive in the Computer browser and clear the fields.

---


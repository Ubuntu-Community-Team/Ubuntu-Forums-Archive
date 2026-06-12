---
title: "Files with name using non-Western characters in the NTFS partition"
date: 2007-07-04
forum: General Help
---

### Post by Gan on 2007-07-04
My NTFS partition contains files and folders with name using non-western characters. These files cannot be shown in the default mounting of the NTFS partition. Where should I change the setting such that they can be read?

---

### Post by ago on 2007-07-04
You'd need to mount/remount with the appropriate utf locale option

mount -t ntfs-3g /dev/# /mntpoint -o locale=en_US.utf8

Note that /host/media might be problematic to remount

---

### Post by Gan on 2007-07-27
> **ago said:**
> You'd need to mount/remount with the appropriate utf locale option

mount -t ntfs-3g /dev/# /mntpoint -o locale=en_US.utf8

Note that /host/media might be problematic to remount
That's /meda/host that I was referring to.
I tried to remount it but got the same result: no non-western chars.
Is there any place I can change the default mounting option (ie. the one before booting ubuntu)?

---

### Post by tuxcantfly on 2007-07-28
> mount -t ntfs-3g /dev/# /mntpoint -o locale=en_US.utf8

If it's non-western characters you want, you'll have to substitue the en_US.utf8 with your locale. To find out what it is, enter this command:

```
locale | grep LC_ALL | sed "s/=/\n/" | tail --lines 1
```

> Is there any place I can change the default mounting option (ie. the one before booting ubuntu)?

That would only work by adjusting your initrd, which is a rather complex process... I'd say just mount it over to a different location with the correct parameters, and access it through there; if you need it mounted on bootup you can add it to /etc/fstab

---

### Post by Gan on 2007-07-31
> **tuxcantfly said:**
> If it's non-western characters you want, you'll have to substitue the en_US.utf8 with your locale. To find out what it is, enter this command...
Thanks. I tried but it didn't work. :(

Actually I have another external hard disk using NTFS, and it is mounted correctly (ie. all file names were shown).

That's what I saw when I typed mount
```
/dev/sdb1 on /media/EXTERNAL type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/remnt type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

Any idea?

---


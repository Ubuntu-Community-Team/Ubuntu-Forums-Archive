---
title: "Double entries in kwikdisk and kdiskfree"
date: 2006-11-18
forum: General Help
---

### Post by akudewan on 2006-11-18
After upgrading to Edgy, kwikdisk and kdiskfree show me double entries for mounted windows partitions.

Kdiskfree shows names like UUID=A8AF-8361 , which the edgy upgrade added/changed to my /etc/fstab file.

Here's a screenshot:
[[IMG]http://img221.imageshack.us/img221/2114/kdiskfreeno6.th.png[/IMG]](http://img221.imageshack.us/my.php?image=kdiskfreeno6.png)

This doesn't actually cause any problems, but its quite annoying. Why is this happening? Any way to fix this?

Here's my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=12bde064-7b67-41bb-8f3a-586dba70d205 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=0d57adff-1f31-4cf5-901b-3bd32c44705d /home ext3 defaults 0 2
# /dev/hdc3 -- converted during upgrade to edgy
UUID=738c3dcb-0f49-452d-944f-eb39f87f367d none swap sw 0 0
# /dev/hda1 -- converted during upgrade to edgy
UUID=5415-0376 /mnt/c vfat auto,user,exec,rw,umask=0000 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=A8AF-8361 /mnt/ranjan vfat auto,user,exec,rw,umask=0000 0 2
# /dev/hdc1 -- converted during upgrade to edgy
UUID=C891-2A4F /mnt/windows vfat auto,user,exec,rw,umask=0000 0 2
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by MWAAAHAAA on 2006-11-19
Same here, KwikDisk shows double entries. Perhaps it has to do with commented entries in /etc/fstab. I have not tried removing those yet though, will do now.

---

### Post by MWAAAHAAA on 2006-11-21
> **MWAAAHAAA said:**
> Same here, KwikDisk shows double entries. Perhaps it has to do with commented entries in /etc/fstab. I have not tried removing those yet though, will do now.

Did not work.

---

### Post by akudewan on 2006-11-22
The shell command "df -h" does not show double entries. Maybe this is a problem with just Kdiskfree and kwikdisk ? a bug ?

---


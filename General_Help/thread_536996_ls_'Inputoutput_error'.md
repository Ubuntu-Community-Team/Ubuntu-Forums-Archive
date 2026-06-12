---
title: "ls 'Input/output error'"
date: 2007-08-28
forum: General Help
---

### Post by Ubuntist on 2007-08-28
I dual-boot Ubuntu and XP.  Using Ubuntu, when I do
```
ls /media/hdc1/WINDOWS/system32/drivers
```I get the response
> ls: drivers: Input/output errorDoes that mean I've got disk problems?

---

### Post by ddrichardson on 2007-08-28
You sometimes get this error with file permission problems. Can you post your /etc/fstab?

---

### Post by Ubuntist on 2007-08-28
Here 'tis:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc5
UUID=d11ee00b-84aa-4b7c-a045-06e99a78da18 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc6
UUID=16e1aec4-8c1f-4379-8880-4034eb415d6d /home           ext3    defaults        0       2
# /dev/hdc1
UUID=AEE4C033E4BFFF97 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc7
UUID=caa5a329-64ae-4512-8e7e-4255fab65867 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto        rw,user,noauto  0       0
usbfs           /proc/bus/usb   usbfs devgid=14,devmode=0660 0      0

```

---

### Post by ddrichardson on 2007-08-28
I don't think it's a permission problem because the umask value is set to 007, which translates to permissions of 770.

What dmesg output relating to /dev/hdc1 is there?

If you dual boot with Windows, does scandisk pass on this drive?

---


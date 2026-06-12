---
title: "syslinux problem"
date: 2008-05-23
forum: General Help
---

### Post by reyhan on 2008-05-23
i want to install Syslinux on my usb but when i type this code

```
syslinux /dev/sdb

```

and it said 
> syslinux: this doesn't look like a valid FAT filesystem

whats happen here? 
oh yeah and i format my Usb by Fat16 partition...

---

### Post by VMC on 2008-05-23
> **reyhan said:**
> i want to install Syslinux on my usb but when i type this code

```
syslinux /dev/sdb

```

and it said 

whats happen here? 
oh yeah and i format my Usb by Fat16 partition...

I usually format my USB sticks to Fat32. How did you format it. Using Windows or Linux?

---

### Post by reyhan on 2008-05-23
i format it using windows

---

### Post by wootah on 2008-05-23
You might want to consider reformatting the stick into FAT32. FAT16 only has a max filesystem size of 2GB--which might be an issue if your stick is bigger than that (wasted space).

I think the tool is probably expecting FAT32--using FAT16 is a little outdated :)

---

### Post by ibuclaw on 2008-05-23
Try:
```
extlinux -i /path/to/mount
``` instead.
At least, I think...

Then run this command to make it bootable:
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
```
That is "**sdb**" on the end, **NOT** "sdb1"

[EDIT]
[Yep, I'm right...](http://sudan.ubuntuforums.com/showthread.php?t=740924)

Regards
Iain

---


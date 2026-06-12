---
title: "Cannot mount External 400gb Hard Drive"
date: 2007-05-11
forum: General Help
---

### Post by Iztari on 2007-05-11
[SIZE="4"]Hello I have a Seagate External Hardrive which work perfectly in Edgy Eft but since I upgraded to Feisty Fawn (fresh install) it doesn't mount automaically and there is no way of opening it.
This is my  fdisk -l:
```

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801    c  W95 FAT32 (LBA)
```

I'll be happy if anybody can help me, I have tried different stuff that I have found in the forums and nothing has work. 
Thanks 
[/SIZE]

---

### Post by taurus on 2007-05-11
```
sudo mkdir /media/windows
sudo mount -t vfat /dev/sda1 /media/windows -o iocharset=utf8,umask=000
df -h
```

---

### Post by Iztari on 2007-05-12
[SIZE="4"]Thanks[/SIZE] a lot that work perfectly :)

---


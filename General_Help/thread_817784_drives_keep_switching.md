---
title: "drives keep switching"
date: 2008-06-03
forum: General Help
---

### Post by AliTabuger7 on 2008-06-03
Ever since my upgrade from Gutsy to Hardy, my drives have been renaming themselves. I have 3 drives, and they seem to randomly choose a name (sda1, sdb1, sdc1). Even the drive Ubuntu is on sometimes gets renamed.

It seems like every time I reboot my symlinks fail because the partitions have swapped their mountpoints. I often try to fix this in /etc/fstab, but they switch again. Sometimes "sudo mount -a" doesn't work because fstab is now trying to mount a ext3 drive as if it were ntfs.

I think it has something to do with dualbooting. I used to just hit escape and select my windows drive (it's a bios feature), but I have it set up now so that grub handles it. I thought this would fix it, but it hasn't.

---

### Post by Rocket2DMn on 2008-06-04
In fstab you can use UUIDs rather than /dev locations, and since UUIDs don't change, this should set you straight.  You can see the UUIDs of partitions by running
```
sudo blkid
```
Then in fstab change the first column for each partition from
```
/dev/sd**
```
to
```
UUID=<uuid_here>
```

---

### Post by AliTabuger7 on 2008-06-06
Wow, Thanks. I can't believe it was that simple.

---


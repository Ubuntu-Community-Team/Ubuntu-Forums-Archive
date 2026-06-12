---
title: "saving ubuntu partition with partimage in dual boot.."
date: 2008-05-28
forum: General Help
---

### Post by Mia_tech on 2008-05-28
I have a laptop with xp and ubuntu installed and I've booted up with systemrescuecd to save the ubuntu partition to the xp, with partimage, but the problem is that I haven't been able to mount the xp(ntfs) partition with read/write access, and therefore not able to save to that partition, could someone recommend me a way to do this?

thanks

---

### Post by bodhi.zazen on 2008-05-28
On the live CD:

```
sudo umount /dev/sda1 
sudo mount -t ntfs-3g /dev/sda1 /mnt -o umask=000
```

Windows is now mounted at /mnt

Assuming windows is on /dev/sda1, adjust accordingly.

I you do not know where windows is 

```
sudo fdisk -l
```

---


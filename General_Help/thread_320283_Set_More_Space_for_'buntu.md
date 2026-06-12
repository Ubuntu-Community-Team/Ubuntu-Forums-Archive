---
title: "Set More Space for 'buntu"
date: 2006-12-17
forum: General Help
---

### Post by hadiriazi on 2006-12-17
Hi guys

This is the result of df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             3.8G  3.4G  247M  **94%** /
varrun                506M  144K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  8.0M  498M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda8              96M   13M   78M  14% /boot
/dev/disk/by-uuid/2EB843B9B8437E79
                       31G   12G   19G  40% /media/sda1
/dev/disk/by-uuid/D8BC8DB7BC8D9124
                       41G   19G   22G  47% /media/sda5
/dev/disk/by-uuid/6C54979154975D20
                       41G   40G  254M 100% /media/sda6
/dev/disk/by-uuid/C0A8A033A8A02A3C
                       35G  2.2G   33G   7% /media/sda7

```

I want to set more space, what should I do?

---

### Post by aysiu on 2006-12-17
I'd try these: ```
sudo apt-get clean
rm -r /tmp/*
```

---

### Post by hadiriazi on 2006-12-17
> **aysiu said:**
> I'd try these: ```
sudo apt-get clean
rm -r /tmp/*
```

I know I could clean the apt cache and also temp files but I want a permanent solution to this. Like increasing the partition size if possible.

Thanks

---

### Post by aysiu on 2006-12-17
Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by hadiriazi on 2006-12-17
> **aysiu said:**
> Can you post the output of this command? ```
sudo fdisk -l
```

```
Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3939    31639986    7  HPFS/NTFS
/dev/sda2            3940       19456   124640302+   f  W95 Ext'd (LBA)
/dev/sda5            3940        9166    41985846    7  HPFS/NTFS
/dev/sda6            9167       14393    41985846    7  HPFS/NTFS
/dev/sda7           14394       18947    36579973+   7  HPFS/NTFS
/dev/sda8           18948       18960      104391   83  Linux
/dev/sda9           18961       19456     3984088+  83  Linux

```

---

### Post by aysiu on 2006-12-17
Hm. The Linux partitions are at the end, so resizing those to make those larger could be tricky. Where would you get the space from--deleting one of your NTFS partitions? /dev/sda7, perhaps?

---

### Post by hadiriazi on 2006-12-17
> **aysiu said:**
> Hm. The Linux partitions are at the end, so resizing those to make those larger could be tricky. Where would you get the space from--deleting one of your NTFS partitions? /dev/sda7, perhaps?

Hi there thanks for your replies. I could resize the sda7 partition then use the free space and give it to my 'ubuntu partition. I just need to know how to bring up gpart and do it and wither or not it's possible?

---

### Post by Ramses de Norre on 2006-12-17
You could make a separate /home partition maybe? It's very useful for backups and will probably move a lot of data from / to /home.

---

### Post by maxamillion on 2006-12-17
Boot into the liveCD (currently listed as Desktop CD) and use gparted (Gnome Partition Manager) and just graphically drag partitions to their desired size with its pleasant GUI tool.

Just my recommendation, I enjoy keeping things simple when possible and I think drag and drop is about as easy as it gets (don't flame me about cli tools, I'm just as big of a cli junkie as the rest but even those who <3 the cli can admit that gparted is a nice tool)

/me

---


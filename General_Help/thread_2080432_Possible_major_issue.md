---
title: "Possible major issue"
date: 2012-11-04
forum: General Help
---

### Post by manjam2 on 2012-11-04
HI Guys! I'm a little freaked out. Let me explain:

I had problems installing ubuntu to my internal hard drive so I downloaded it to my external drive. I did do any partitioning, just installed it. Ubuntu works fine but I can't acess the drive on my Windows PC or on Ubuntu. My drive had all my fasmily photos on it and I don't want to have to tell my family I deleted out photos out of stupidity. Are those pictures still there? I just need to know.

---

### Post by mr_luksom on 2012-11-04
Hi Manjam,

Can you clarify what you mean by 'just installed it'? There are a few options in the setup process that determines where it gets installed.

---

### Post by manjam2 on 2012-11-04
I'll be honest with you. I didn't create a new partition, I just clicked on the drive I wanted UBuntu to boot from and it installed to that drive. The drive in this case was the external drive with my pics on it.

---

### Post by idoitprone on 2012-11-04
> **manjam2 said:**
> I'll be honest with you. I didn't create a new partition, I just clicked on the drive I wanted UBuntu to boot from and it installed to that drive. The drive in this case was the external drive with my pics on it.

it is simpler if you post this

```
sudo fdisk -l
```

---

### Post by mr_luksom on 2012-11-04
Are you still in ubuntu? Can you post the output of the following command:

```
sudo fdisk -l
```

---

### Post by manjam2 on 2012-11-04
```
 ezra@ezra-FK586AA-ABA-SR5610F:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1522

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
/dev/sda5          501760   625141759   312320000   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ba23

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   306554879   153276416   83  Linux
/dev/sdb2       306556926   312580095     3011585    5  Extended
/dev/sdb5       306556928   312580095     3011584   82  Linux swap / Solaris

```

That's what I get.

---

### Post by manjam2 on 2012-11-04
I tried plugging the drive into windows on my other computer, but it isn't readable for some reason. I hope you guys will be able to help me. I'm getting really scarred about this.

---

### Post by idoitprone on 2012-11-05
> **manjam2 said:**
> I tried plugging the drive into windows on my other computer, but it isn't readable for some reason. I hope you guys will be able to help me. I'm getting really scarred about this.
I do not know what to say. You have overwritten your windows partition. Test disk will not help because installing the os mean your overwritten the data

---


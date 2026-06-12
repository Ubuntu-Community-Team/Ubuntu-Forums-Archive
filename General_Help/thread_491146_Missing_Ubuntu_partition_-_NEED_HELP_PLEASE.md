---
title: "Missing Ubuntu partition - NEED HELP PLEASE"
date: 2007-07-03
forum: General Help
---

### Post by imprezagtr on 2007-07-03
Hello,

I have recently installed Ubuntu 7.04 in a Win XP Pro machine. GRUB was the default OS selector whenever I boot up the machine. I allocated 20 GB out of 40GB for Ubuntu and the rest is Win XP. I don't know what I did to the ubuntu partition (I really didn't do anything besides updating it with automatic updates and using it daily), but now the partition is gone. I tried using a live CD, installing Acronis Disk Director 10, but none of them see the ubuntu partition! I know it's there besides Win XP still only has 20GB of total size. Is there anyway I can recover that "lost" partition or even detect it?? I'm a noob, so please explain the steps as detailed as possible if you can. 

Thanks alot in advance.

Will

---

### Post by LaRoza on 2007-07-03
Go to the Windows tool "Disk Management" and see what it says about your disk.

Does it say anything like "unallocated space"?

-What does Grub say at startup?

---

### Post by bodhi.zazen on 2007-07-03
Actually, boot the ubuntu, desktop CD and either run gparted or in a terminal enter :

```
sudo fdisk -l
```

In all likelyhood your ubuntu partition is just fine, windows can not read it.

If you want to access the partition from windows : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by imprezagtr on 2007-07-05
@LaRoza,

In Windows, it doesn't show unallocated space at all. just one partition, which is the NTFS where win xp is using. There's no GRUB. Like I said previously, i think the GRUB disappeared. When PC starts, it just go straight to Win XP like it's the only OS installed.

@bodhi.zazen,

I tried gparted, but it doens't show two partition. Below it shows the following:

partition         file system        size             used               unused        flags
/dev/sda1        ntfs               37.27Gib     28.66GiB         8.60Gib        boot


I allocated 20Gb to each OS, so obviously it's seeing two partitions combined... but in win xp, it shows only 20GB max allocated to that. 

any other ideas??? Thanks.

---


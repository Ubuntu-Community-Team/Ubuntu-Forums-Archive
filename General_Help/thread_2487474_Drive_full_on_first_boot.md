---
title: "Drive full on first boot"
date: 2023-06-06
forum: General Help
---

### Post by dlav09 on 2023-06-06
Hello,

I installed an Ubuntu based distro on an SBC with a 64GB eMMC.

At the first start, I have a warning message telling me that I have no more space and that I cannot install large software. Yet the disk is only 15GB while the storage is 64GB

Comment is it possible?
How to correct this?






```

rock@r58:~$ df
Filesystem                1K-blocks            Used        Available      Use%       Mounted On   
/dev/mmcblk0p1            306580            142884         163696        47 %             /boot 
/dev/mmcblk0p2            15016152        13122848        1714556        89 %             / 

```

---

### Post by TheFu on 2023-06-06
Could the eMMC be full of bad blocks?

For our sanity and so nobody makes a bonehead column mistake, please post the output from these two commands, wrapped in forum code-tags so the columns align correctly.  I've used code tags below, so if your post doesn't look like that, please fix it.  There's no need to manually change columns or insert spaces. If you do that, then that isn't using code-tags- the advanced editor of this forum as a button (#) for code tags.

```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

And please, please, include the command and the headers that the output includes for each column.

---

### Post by dlav09 on 2023-06-06
I edited the post, hope it's correct now.


Is it normal that the /dev/mmcblk0p2 partition is only 15 GB on first boot while the eMMC is 64 GB?

---

### Post by tea for one on 2023-06-06
> **dlav09 said:**
> I installed an Ubuntu based distro on an SBC with a 64GB eMMC.
Which distro?
> At the first start, I have a warning message telling me that I have no more space and that I cannot install large software. Yet the disk is only 15GB while the storage is 64GB
Comment is it possible?
Certainly possible if you created your own partition sizes during the installation
> How to correct this?
Boot into a live session and use the partition manager to increase /dev/mmcblk0p2

---

### Post by TheFu on 2023-06-06
> **dlav09 said:**
> I edited the post, hope it's correct now.


Is it normal that the /dev/mmcblk0p2 partition is only 15 GB on first boot while the eMMC is 64 GB?

Thanks for editing, but it isn't the exact commands with the options requested.  This provides facts that haven't been shown, yet.

As for sizing of different partitions, I've seen all sorts of odd sizes setup by the default settings.  About 3 yrs ago, I gave up with the defaults and always layout exactly what I desire before getting to the disk part of the installation tasks.

There are very different defaults for BIOS booting, UEFI booting, LVM use, non-LVM use, ZFS, BTRFS and encryption.  I suspect each Ubuntu Flavor also has their favorite layout they inflict on people choosing the defaults.  IDK.

MMC devices do fail, eventually. That's my current guess based on what's been provided so far. More facts from the requested commands being run and posted would quickly answer many of my questions.  I'll have more after seeing the output, probably.

---


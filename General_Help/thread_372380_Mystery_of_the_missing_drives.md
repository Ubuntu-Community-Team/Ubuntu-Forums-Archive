---
title: "Mystery of the missing drives"
date: 2007-02-28
forum: General Help
---

### Post by HessiaNerd on 2007-02-28
Ok, so apparently Ive been doing a bit to much mucking around with my mounts.

two of my drives disappeared from my /dev folder.  They are both IDE drives my main drive is SATA and one is ntfs, one ext3.  I'm not exactly sure when this happened but I know that I was able to read from both, and write to the ext3 drive a couple of days ago.  Now neither are mounted, and when I try to remount they wont, cause they wont appear in /dev

```


 sudo mount -a
mount: special device /dev/hdc1 does not exist
mount: special device /dev/hdd1 does not exist

~$ fdisk -l
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)

~$ ls /dev/h*
/dev/hda  /dev/hpet  /dev/hwrng


```

the drives were hdc1 and hdd1:

Once again,, any advice as to where I might begin looking would be extremely helpful.

---

### Post by sadako1 on 2007-05-29
I just had a similar problem but it's fixed now.

Do you tend to 'hibernate' your windows installation instead of doing a full shutdown? That was my problem. I rebooted Windows and shut down properly. Problem solved!

Andrew

---


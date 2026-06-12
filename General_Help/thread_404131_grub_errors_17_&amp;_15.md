---
title: "grub errors 17 &amp; 15"
date: 2007-04-08
forum: General Help
---

### Post by moot on 2007-04-08
My Ubuntu machine has two hard drives, one internal SATA hard drive and one external USB hard drive.  I finally got tired of trying to dual-boot XP and Ubuntu on my internal SATA HDD, so I backed-up everything I needed onto my Ubuntu partition as well as two other computers and copied the XP partition to my external HDD using gparted and then deleted the XP partition off of my internal SATA drive.  In case that was confusing, here's how I had everything configured back then:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1                63         9729     (I forgot)     7    HPFS/NTFS
/dev/sda2   *        9730       18947    74043585   93  Linux
/dev/sda3           18948       19457     4096575   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             1       24792   199141708+   7  HPFS/NTFS
```


And how I have everything configured now:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        9730       18947    74043585   93  Amoeba
/dev/sda3           18948       19457     4096575   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             1       24792   199141708+   7  HPFS/NTFS
```


As you can plainly see, "Amoeba" is not Linux.  When I rebooted I got the dreaded grub error 17:

```
GRUB Loading stage1.5

GRUB loading, please wait...
Error 17
```


I followed the directions for restoring GRUB from a LiveCD found here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


But after I chroot into /dev/sda2 I get the following error whenever I try to use sudo grub:

```
root@ubuntu:/# sudo grub
sudo: unable to lookup ubuntu via gethostbyname()
```


And when I try to use grub without sudo after chrooting into /dev/sda2 and attempt to look for /boot/grub/stage1 I get grub error 15:

```
Error 15: File Not Found
```


I can clearly see /boot/grub/stage1 on /mnt/root/boot/grub/stage1 in Nautilus but grub can't find it even after I did all of that other stuff the thread I linked to said to do.  My questions are, how can I get grub to work again so that I can boot into my Ubuntu partition, and once I get there, how can I configure grub so that it also lists the Windows XP Professional partition on my external HDD in the boot list so that I can boot off of that too if I want to?

---

### Post by moot on 2007-04-08
Bump.

Edit: I checked out some other threads where people had similar problems and I discovered that hiding your Linux partition changes it to an Amoeba partition and that you can change it back by changing the partition Id from 93 to 83 using fdisk.  I tried this and I'm not sure if it worked or not, sudo fdisk -l still shows it as an Amoeba partition and parted shows it as an ext3 partition that isn't hidden.  Would changing the flag from boot to something else like root solve the problem?

---

### Post by zvacet on 2007-04-08
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

---

### Post by moot on 2007-04-08
For some reason users.bigpond.net doesn't load for me, I checked the google cache of the website though and it might be the solution I'm looking for, thanks.

Edit: Apparently you have to write your changes to the partition table with x before you can exit fdisk, otherwise it won't save them.  Now it lists my Linux partition as Linux and not Amoeba.  After I did this I was able to re-install grub to the MBR with no problems.

---

### Post by moot on 2007-04-08
One last thing, I'm posting from my Linux partition now, but as I mentioned earlier I deleted /dev/sda1 (My former Windows XP parititon) and now it's just a bunch of un-used space on my internal HDD, space that I want to give to Linux (/dev/sda2).  How do I go about giving this un-used space to Linux?

---


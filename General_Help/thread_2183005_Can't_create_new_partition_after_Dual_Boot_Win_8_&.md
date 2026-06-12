---
title: "Can't create new partition after Dual Boot Win 8 &amp; Kubuntu"
date: 2013-10-23
forum: General Help
---

### Post by tommysmith2 on 2013-10-23
Hi, I make a Dual Boot with Kubuntu 13.10 and Win 8.1, and the problem is my HDD 400Gb, I created each of them 50Gb and the result :

```


/dev/sda1    ntfs          System Reserved     350Mb

/dev/sda2    ntfs          Win 8.1                  50Gb

/dev/sda3    extended   swap                     4Gb

/dev/sda4    ext4          Kubuntu                50Gb

[B]Unallocated Unknow                                 270Gb

[/B]
```

So when I tried to format new free partitions above, I get error messenger : Already 4 primary and this is maximum number its partition table can handle....

How can I solve the problem ? I just think we can created many small partitions logical / extend much I want :confused:

Thanks for any help :)

---

### Post by TheFu on 2013-10-23
1 of the primary partitions must be "Extended" - that means you only get 3 primary partitions, since the 4th would be "extended" and would contain as much of the HDD inside as you'd want to hold 100+ logical partitions.

OTOH, if you use UEFI, then you can use GPT partitions that don't have any real partition count limitations like MBR-based partitions. Migrating to GPT is a complex thing on an existing HDD.  Windows will not boot off GPT except if:
a) UEFI BIOS
b) 64-bit windows
c) winXp is not supported
d) older - pre-2012-ish - Linux is not supported.

There are a few other options, more complicated and Linux-only. Having Windows really limits the options.

The wikipedia articles on "MBR" and "GPT" would be good to review to gain better understanding.

---

### Post by oldfred on 2013-10-23
Swap and all the other partitions you want should be inside the extended. 
But you can only have one extended partition and all logical partitions must be in that one extended. Or no primary partitions can be in the middle of the extended.

I usually put swap at end or far right of drive, rarely used anymore with most systems with decent amounts of RAM. And make the entire far right part of drive when viewed in gparted as the extended with many logical partitions.

Blue border also shows extended partition. You need to have your Kubuntu inside the extended. You can convert it to logical with fixparts or if you have not installed just delete it, expanded extended to include entire rest of drive and then recreate it.

---

### Post by tommysmith2 on 2013-10-23
@TheFu: Thanks your help. I install in laptop Toshiba A300 and unlucky it not use UEFI boot :(

@oldfred: I install a fresh Win 8 and Kubuntu, so I can install it again, could you help me the best way to reinstall two of them with GPT or like your partitions can boot with multiple OS later !?! I install Win 8 for testing and just install some software not much, so I can't deleted it anytime, I just want to using Kubuntu for main OS later. Thanks :)

---

### Post by TheFu on 2013-10-23
Windows8 cannot boot from a GPT disk without UEFI. Sounds like you are stuck with MBR and 3 primary partitions + 1 extended. You'll need to make rooms.

---

### Post by oldfred on 2013-10-23
I do not know how to install Windows 8. 

But if your system is not UEFI, you cannot use gpt. Windows only boots from gpt partitioned drives with UEFI.
Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS modes, if you have correct partitions. 
If not a laptop, I would suggest Windows on a MBR drive and Ubuntu on a gpt drive, but with one drive you will have to use MBR and BIOS boot.

So just expand your extended partition to include rest of drive and put logical partitons in the extended partition.

---

### Post by tommysmith2 on 2013-10-24
Windows suck, the more newer version the more heavier for machine and money, I just install it for testing to support customer when they needed, it's so heavy that can't install in my Virtualbox @@

I had reinstall Kubuntu, merge with unallocated partitions and resize after installed two partitions - one for Kubuntu, and one for ntfs just for storage data. But I have some question, I don't know why I can see, can use and format it become ntfs in Kubuntu, but when I switch in Win 8 and check it in Devide manage, it's just show that partition is a Unallocated and can't use, format or do anything !?!

Moreover, I'm quite newbie with partitions, I don't understand why first time install Kubuntu, it's show that a primary partitions, but in this time, after merge, it's show a extended partitions !?

---

### Post by oldfred on 2013-10-24
I always use gparted, not sure if same partition tools are available with Kubuntu or not. But if NTFS is inside your extended partition you cannot work on it when booted as the entire extended is considered mounted if any logical partition is mounted. 
You can use liveDVD or flash drive (with Kubuntu you may have to install it) or download gparted or partedmagic liveCDs. You may still have to swapoff to unmount swap as live installer mounts swap to speed things up a bit. I do not think gparted liveCD mounts swap.

---

### Post by tommysmith2 on 2013-10-25
Oh, Kubuntu don't have gparted, I had download and installed it later. Uhm, but have problem that Kubuntu can see but can't access the Windows partitions, and the Windows also can't access the Data partitions ntfs that I had format and show in the picture below:

[ATTACH=CONFIG]247243[/ATTACH][ATTACH=CONFIG]247242[/ATTACH][ATTACH=CONFIG]247244[/ATTACH]

Ah, How could I make those thumbnails bigger :D

---

### Post by oldfred on 2013-10-26
Windows should be able to access your NTFS partition. But it may need chkdsk if you resized it from outside Windows.
Generally the Linux NTFS driver will not mount NTFS partitions that need chkdsk or are hibernated to prevent damage. Also the drive exposes all normally hidden files in Windows so best to mount the c: drive as read only or not mount at all.

---


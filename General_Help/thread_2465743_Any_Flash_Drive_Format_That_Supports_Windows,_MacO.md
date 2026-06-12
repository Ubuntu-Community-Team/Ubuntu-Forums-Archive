---
title: "Any Flash Drive Format That Supports Windows, MacOS &amp; Ubuntu Please?"
date: 2021-08-10
forum: General Help
---

### Post by amyni on 2021-08-10
Hi. I already have a Mac & one Windows laptop. I am planning to install Ubuntu & remove Windows from the laptop as I want to use Ubuntu for coding practice & learning Linux server related things. I have one external hard drive which I use to port files from Mac to Windows. I formatted the device using exFAT format as mentioned [here]("https://www.w3spot.com/2021/05/how-to-use-flash-drive-in-both-macos-and-windows.html"). It works fine in both of my laptops now. But I am not sure if exFAT can be detected by Ubuntu. Before installing Ubuntu I want to make sure I have the right file format in my flash drive. Is there a file system which can support Windows, Mac & Ubuntu? I am fine with a file system which can be detected by both Mac & Ubuntu for now. At least that will suffice my current situation.

---

### Post by oldfred on 2021-08-10
There is exFAT support. Older kernel  test:
exFAT File-System Performance On Linux 5.9  Nov 2020
[https://www.phoronix.com/scan.php?page=article&item=exfat-linux-59&num=1](https://www.phoronix.com/scan.php?page=article&item=exfat-linux-59&num=1)

The standard exFAT implementation is not journaled and only uses a single file allocation table and free space map. 
But exFAT will store larger files than FAT32. But still should not be used for larger partitions as chkdsk may take forever. 
And it does not have Linux ownership & permissions.

---

### Post by sudodus on 2021-08-10
+1 to exFAT as a file system that works in current versions of all three operating systems: Ubuntu (linux), Windows, MacOS.

I don't know MacOS well enough, but I would guess, that it can read/write at least some free file system, that works with Linux too. UDF is a trivial example, but I think there is very weak support for it, for example no good tools to repair it. After some web browsing I found a promising link at superuser,

[Which file system to use in between OSX and Linux?](https://superuser.com/questions/392702/which-file-system-to-use-in-between-osx-and-linux)

The accepted answer recommends HFS+ (journaled), so use Disk Utility.app on your Mac to format the partition with HFS+ (journaled).

---


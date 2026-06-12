---
title: "How to &quot;convert&quot; a completed BIOS mode install to UEFI? --mini.iso"
date: 2015-02-22
forum: General Help
---

### Post by garycheng12 on 2015-02-22
Goal: Have a UEFI system with only plasma-desktop installed. Seems like this can only be accomplished with a mini.iso.

Problem: Mini.iso can't be used on a UEFI system (UEFI system can use mini.iso, but only through BIOS--how to have a system with only plasma-desktop installed while utilizing the advantages of UEFI)?

Semi-related question: What else is different between Ubuntu and Kubuntu *besides* the desktop environment and default list of applications such that I may prefer Ubuntu with KDE without pre-installed applications? The above scenario of mini.iso + plasma-desktop = **Ubuntu with KDE without pre-installed applications**. *What* gets me **K**ubuntu with the default KDE without pre-installed applications, or is it literally the same in every aspect and no Linux user would prefer one over the other? I'm concerned about any implications that may exist of having either the Ubuntu or Kubuntu *label. *On Kubuntu's wiki page, I see that besides the difference in DE and applications, Ubuntu uses Nux and GTK+ toolkits. Also, they have different developers so choosing Kubuntu or Ubuntu may depend on the difference of things other than DE and applications.

---

### Post by oldfred on 2015-02-22
I believe you could use the server version.

If you create partitions in advance using gpt partitioning and install in BIOS mode, you can convert to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI). Boot-Repair from live installer booted in UEFI mode can walk you thru the total grub uninstall and reinstall process. 

Some related info, but more discussing flash drive install:
[https://www.kubuntuforums.net/showthread.php?63131-Bootable-USB-stick](https://www.kubuntuforums.net/showthread.php?63131-Bootable-USB-stick)

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---


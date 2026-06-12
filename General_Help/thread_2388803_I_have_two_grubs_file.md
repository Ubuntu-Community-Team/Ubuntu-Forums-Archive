---
title: "I have two grubs file"
date: 2018-04-07
forum: General Help
---

### Post by No peacE on 2018-04-07
Hi all,
I'm using ubuntu 16.04 LTC, I install opensuse 42.3 alongside with ubuntu (shered home folder) and Windows10, but now I have two grubs, one for ubuntu which is not detect the new operating system, and the other one is for opensuse.

How can I merge two grubs in one grub?

---

### Post by oldfred on 2018-04-08
UEFI or BIOS.
All systems must be in same boot mode, or you cannot use one grub.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Also best not to share /home as configuration in one system may not be what you want in the other. You can create a /mnt/data partition with all your data and share that. Back with XP I had both an NTFS shared and Linux formatted shared data partition. Windows 10 makes it a bit more difficult with its fast boot/hibenation and its updates turning that back on. If hibernation on Linux will not mount NTFS read/write.

---

### Post by &amp;wP*!) on 2018-04-08
Sharing home folder is not a good practice, because several desktop or user based settings could cause conflict on both. Setting on one operating system might not work on the other. 

Backup all personal data in /home to a separate mount. This mount should be accessible by both systems. The difference is that there won't be config files in it (/home/user will always have hidden files like .gtk etc which might cause problems). This has been also recommended by the other post above.

---


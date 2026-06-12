---
title: "HOWTO repair Corrupt Partition?"
date: 2015-02-10
forum: General Help
---

### Post by sobri.official on 2015-02-10
Hello, i'm having this problem since 2 weeks ago. Whenever I open my netbook it will go direct to bios. I tried to format gparted but failed. it says partition is unallocated. Someone please help me. I don't know what to do. Thanks in advance - [http://paste.ubuntu.com/10159124/](http://paste.ubuntu.com/10159124/)

---

### Post by carl4926 on 2015-02-10
You had Ubuntu installed and then formatted it away?
How you just get BIOS?

Sounds like you need to re-install

---

### Post by oldfred on 2015-02-10
You are not showing any partitions?

Is hard drive failing? Even newer drives can fail. I would use Disks and click on tiny icon on upper right and see if Smart Status says drive is ok or not.

Then you could try testdisk to see if it shows anything. You probably need deeper search. But was system UEFI or BIOS? On of the first questions testdisk asks is if gpt or MBR(mdos). If UEFI system then gpt is correct, if BIOS then MBR is correct. Wrong choice will not find any partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

But at this point, best choice is reinstall and restore all your data from your backups.

---

### Post by cl-netbox on 2015-02-10
Boot from ubuntu install media and open GParted.
Delete all partitions and create a new partition table.
Choose gpt when you want to install ubuntu in EFI mode.
Choose msdos when you want to install in legacy mode.
Create new partitions (if you want to) and start installing.
This worked for me in a similar situation; hope that helps.

---


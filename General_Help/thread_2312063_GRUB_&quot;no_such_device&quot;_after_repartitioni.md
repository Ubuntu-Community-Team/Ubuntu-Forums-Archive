---
title: "GRUB &quot;no such device&quot; after repartitioning"
date: 2016-02-01
forum: General Help
---

### Post by grzechol2 on 2016-02-01
Hi guys,

Here's my story:

I have one physical HDD with dual boot Windows 8 & Ubuntu 14.04. I resized my partitions using GParted Live, however this broke my GRUB configuration so the only *grub rescue* was available on boot. I used the Rescatux tool ([http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)) to fix it. That restored my GRUB menu, and Ubuntu works perfectly fine, however when I chose Windows 8 I got the following errors:```
Error: no such device: 8270BCAE70BCA9F5.
Setting partition type to 0x7
Press any key to continue...
```
After pressing any key I got:
```
This is not a bootable disk. Please insert a bootable floppy and press any key to try again...
```
I wish I could insert a bootable floppy, but unfortunately my laptop doesn't have a 3,5" floppy drive. So I can only press *any key* again, to see the following message:```

BootDevice Not Found
Please install an operating system on your hard disk.
Hard Disk - (3F0)
F2 System Diagnostics
For more information, please visit: www.hp.com\go\techcenter\startup
```

I thought running *update-grub* will help, but it just removed Windows 8 from the GRUB menu.

How can I fix the GRUB configuration and have Windows 8 working again? Here is the output of *Boot Info Script*: [http://paste.ubuntu.com/14851981/](http://paste.ubuntu.com/14851981/)

Thank you in advance.

---

### Post by oldfred on 2016-02-01
You are missing Windows boot files.
Window needs in the primary NTFS partition with the boot flag bootmgr & /Boot/BCD.

You now show sda1 as FAT16 which is highly unusual. Was that NTFS before. And it probably was as it has boot flag, but does not show now any boot files.
It looks like you have a copy of bootmgr in sda2, your main install, but no BCD. If you create a BCD and move boot flag to sda2 it should boot. You need Windows repair tools, Windows repair disk or a third party Windows repair disk to create new BCD. That cannot be done from Linux.
 
Or perhaps resetting, not reformatting, the partition type of sda1 to 07, so seen as NTFS may work? You can try Disks, and set type, but do not select the format.

---


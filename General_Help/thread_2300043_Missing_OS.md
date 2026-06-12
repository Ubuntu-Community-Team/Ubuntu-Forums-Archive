---
title: "Missing OS"
date: 2015-10-23
forum: General Help
---

### Post by kpmaddenuk on 2015-10-23
Help!

I've been running 14.04.03 for some time on a machine with 2x2TB drives setup as a mirrored RAID. Now when I try to boot I get the message "Missing operating system" and the machine hangs.

The BIOS look OK as both discs can be seen. I can interrogate information about the (hardware) array by using Control-F. So all looks well at a low level.

I've run Ubuntu from a DVD but the disks/array do not show up as being available. I have then tried to re-install.

During re-install the partition table shows the RAID as it should be. When asked to continue the installer tells me that two partitions (data and swap) will be deleted and formatted. At this point I hit "Continue" and then get a message box with the message "**??? ???**". When OK'd the installation halts with no additional information. (The world map is on the screen but "Continue" is grayed out.)

So, in short, HW looks OK; BIOS looks OK; RAID looks OK; UBUNTU sees RAID but it cannot find the OS.

Any help would be gratefully received.

Cheers - SD

---

### Post by oldfred on 2015-10-23
Are you using Desktop installer or server installer?
Did you use the same installer when you originally installed?

It used to be and may still be that Desktop installer does not yet fully support RAID. It used to be with 12.04 that Desktop installer had no RAID nor LVM support. But you could use Alternative installer that had those extra drivers. Then they obsoleted the Alternative installer. You could use Server version and add Desktop of choice. 
But with 14.04, LVM is supported, but I do not specifically see RAID support. But some with RAID do have system see RAID but not install grub, so not fully supported.

You do need Desktop installer to run Boot-Repair or its own liveCD/flash drive.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Do not know RAID, so not sure I can help, but details may help those who can.

---

### Post by kpmaddenuk on 2015-10-23
> **oldfred said:**
> Are you using Desktop installer or server installer?
Did you use the same installer when you originally installed?


That could be it. I can't remember what I used for this but I've done a couple of DT installs on friends laptops since so I may be using the wrong disk. I'll re-burn a server disk and try again.

---


---
title: "Installed new IDE Disk, GRUB won't load"
date: 2006-11-27
forum: General Help
---

### Post by seanUSXIII on 2006-11-27
Hi. I installed a new 200Gb IDE disk into my computer. Upon restarting, GRUB complains of an error 22. However, if I unplug the new disk, it boots just fine. Both disks are set for cable select. I also have a SATA drive, on which ubuntu resides. GRUB wrote to the IDE disk when I installed, so here's the setup:

/dev/sda --> Root SATA disk, Ubuntu is here
/dev/hda --> IDE master, GRUB MBR is here
/dev/hdb --> IDE Slave. This is the disk I want to add, however, GRUB will not boot.

If anyone can help me here, it will be greatly appreciated. I got the disk for $20 on black friday and would like to be able to use this great bargain.

---

### Post by dcstar on 2006-11-27
> **seanUSXIII said:**
> Hi. I installed a new 200Gb IDE disk into my computer. Upon restarting, GRUB complains of an error 22. However, if I unplug the new disk, it boots just fine. **Both disks are set for cable select**.
.

How about you set you Master disk to "Master", and the new disk to "Slave", and see what happens?

---

### Post by pjbgravely on 2006-11-27
I just ran into the same problem on my server. I installed another PATA ( IDE) drive and grub wouldn't boot. I found out that grub seems to count PATA drives before SATA drives or Scuzzys. So when I installed Ubuntu server Grub saw my discs as hd0=hda , and hd1=sda. When I added the second PATA drive as master of the second IDE controller Grub saw it as hd1 and pushed sda to hd2. When that happened it could no longer find it's info in /boot/grub and gave an error.

To fix it I used the [Super Grub boot disk]("http://supergrub.forjamari.linex.org/") to boot the OS ( the repair utilities didn't work but you might as well try them) and then I could run grub-install to make it so Grub that is installed on hda points to sda for it's files.

Paul

---


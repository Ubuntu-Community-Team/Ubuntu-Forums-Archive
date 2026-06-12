---
title: "sata_nv installation problems"
date: 2005-10-24
forum: General Help
---

### Post by coyn on 2005-10-24
I am having some serious problems installing Ubuntu on my machine.  I am attempting to set up a software raid 5 file server with Ubuntu, and am having some hardware difficulties.  There are a few scenarios here, for I have been tinkering with the install for over a week.

normal installation (expert)
The kernel starts up and sits.  Eventually spits out:
ATA5: timeout 0x25 ... ... (Sometimes will say this, sometimes not, currently trying to reproduce the exact message).

When I start the installer with:
expert irqpoll
Then the kernel will start, and repeatedly say:
sata_nv: Primary Device Added
sata_nv: Primary Device Removed
sata_nv: Secondary Device Added
sata_nv: Secondary Device Removed

I then can get into the installer, but it will randomly hang during any one of 3 stages of reading the cd.
1) While Checking the CD
2) While copying modules from CD
3) During installation of Base System

When the hang occurs, the system is frozen.  I cannot check the logs using ALT-F3/ALT-F4, and I cannot access the shell using ALT-F2.  If i can get to the point where I partition my hard drives, the installer sees all 8 of them.  I have tried using other various boot flags such as:
bf26, noapic, nolapic, pci=noacpi, pci=irqroute.

In fact, all of those flags, except bf26, that I have tried in conjunction with irqpoll have led to the installer only seeing 4 of the 8 sata channels.  

I have also tinkered in the BIOS to attempt to find a Legacy Emulation for the Sata drives, have tried using the nvidia fakeraid(apparently the concensus is that md is faster anyway, though could never detect the fakeraid volume).  I have tried turning off dma transfer for the cd-rom.  I am running out of ideas here.  I have tried installing Sarge, and even tried the test release of Sarge.  Sarge boots nicely without irqpoll, but only sees 4 of the 8 sata channels.  I even tried using FC4, which would hang every time it tried to load the sata_nv driver.  I have tried swapping out the cd rom drive.  I have not tried placing a PATA IDE drive in yet.  I will try that next, and attempt to configure the sata raid 5 after the install.  Anyways, any ideas would be appreciated, I am running out of fresh ideas.  Thx.

---

### Post by coyn on 2005-10-26
Well, for those who are interested, I managed to solve the problem.  I ended up disabling 6 of my 8 hard drives and running the installer.  It no longer required the irqpoll option, and I Installed on a small partition on my first hard disk.  I did not configure any users except for root.  I had to start in recovery mode and edit /boot/grub/menu.lst to include irqpoll as a kernel option, then rebooted and enabled the rest of my drives.  Started in recovery mode again and configured the md0 device, added a partition to it, then used: mkfs.ext3 /dev/md0 .  I finally edited the /etc/fstab file to mount md0 as /home.  I added some users and my fileserver seems to be working great.

---


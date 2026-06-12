---
title: "Software Raid problem in Ubuntu 7.10"
date: 2007-10-23
forum: General Help
---

### Post by ferdlz on 2007-10-23
Hello,
I recently installed ubuntu 7.10 on a HP Proliant ML 110G4 server with two SATA Disks.
The root filesystem is a software raid device (raid1) and everything works fine.
I have installed Grub on both harddisks so that the system can boot from either disk. If one of the disks fails.
But if I remove one of the harddrives the System doesn't boot anymore with the following symptoms:
During startup the system waits for the rootfilesystem and after 3 minutes it is kicked out to the busybox. In /proc/partitions I can see that no md device was created.
The kerneloutput is the following:

[   53.093431] md: md0 stopped.
[   53.133699] md: bind<sda1>
[   53.139343] md: md1 stopped.
[   53.160394] md: bind<sda2>
[   53.166071] md: md2 stopped.
[   53.222324] md: bind<sda3>

When starting with both disks connected the md devices are created as can be seen in the output:

[   52.537440] md: md0 stopped.
[   52.537454] md: unbind<sda1>
[   52.537460] md: export_rdev(sda1)
[   52.541974] md: bind<sdb1>
[   52.542127] md: bind<sda1>
[   52.547655] raid1: raid set md0 active with 2 out of 2 mirrors
[   52.547723] md: md1 stopped.
[   52.547731] md: unbind<sda2>
[   52.547735] md: export_rdev(sda2)
[   52.565537] md: bind<sdb2>
[   52.565683] md: bind<sda2>
[   52.571340] raid1: raid set md1 active with 2 out of 2 mirrors
[   52.571403] md: md2 stopped.
[   52.571411] md: unbind<sda3>
[   52.571414] md: export_rdev(sda3)
[   52.622105] md: bind<sdb3>
[   52.622269] md: bind<sda3>
[   52.627933] raid1: raid set md2 active with 2 out of 2 mirrors

Can this be a bug?

---

### Post by Miaooaim on 2007-11-05
Hi,
I'm having exactly the same problem.

Anybody can help us???

Regards
Giuseppe

---

### Post by fjgaude on 2007-11-05
From what I've heard it is a bug. File a bug report.

---

### Post by Ser&#265;jo on 2007-11-26
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/133773]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/133773")

---

### Post by fjgaude on 2007-11-26
Very good... I trust others do not have any more troubles with raid1.

---


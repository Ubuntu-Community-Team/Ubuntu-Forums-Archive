---
title: "Replacing bad motherboard with 16.04 software RAID 5"
date: 2020-05-21
forum: General Help
---

### Post by razzamatazz on 2020-05-21
Hello,

The Tyan S2865 (AMD Opteron) motherboard from an old Ubuntu Server 16.04 file server has died:-(  I'd like to replace with an updated AMD chip and motherboard, but would rather not have to rebuild a rather large software RAID 5 array (data is backed up).  Besides the need for updated drivers, is it possible to get "plug and play" functionality, or will the OS or RAID be affected if I drop in a newer chip/board?

Thank you in advance for any guidance you may have!

---

### Post by TheFu on 2020-05-21
I've moved a 4 disk SW-RAID array 3 times between different physical systems, all with different SATA controllers.

The only real issues will be with NIC driver changes and GPU drivers.  The NIC stuff will happen automatically, unless you pull the old NIC and put it into the new system.  The GPU is something I'd just remove the proprietary drivers from and deal with as it was a new GPU.

If the old system was running any software that was specific to the Opteron, you probably want to change that to the newer Ryzen model.  Hypervisors often care.  I forgot to change the VMs to use AMD CPUs and they failed to start because each was locked to an Intel C2D CPU. The host worked fine.

Regardless, this is a huge change and problems of some sort should be expected.  I would encourage you to ensure the new motherboard has Intel NICs. Those are better supported and more efficient for shipping bits around.  I have a Ryzen5 box and I'm looking at getting another cheap Ryzen5 to replace 2 other systems.

---

### Post by Frogs Hair on 2020-05-21
Experiece above ^^

---

### Post by razzamatazz on 2020-05-21
Thanks for your perspective, TheFu.  This build's sole function was as a headless file server, so gladly no other resources are required beyond basic OS, network, mdadm, and smb.  I've dealt with my share of arrays, but this will be my first time to attempt physically moving a RAID to new hardware; I'm glad to hear you've done it successfully several times.  I do indeed anticipate some issues, but as long as I can boot into the OS and it will take commands, I think I'll be ok.

---


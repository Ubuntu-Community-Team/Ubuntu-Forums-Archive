---
title: "Nvidia nForce2 Ultra + RAID MCP Will not boot from SATA"
date: 2004-12-17
forum: General Help
---

### Post by varnerin on 2004-12-17
I have two SATA 200 GB Maxtor drives. The first drive has XP, and I installed the Ubuntu on the second one. When I installed Ubuntu, I said yes to install grub on MBR. When it boots, it goes directly into XP, no grub.

During the install, it says the SATA drives are SCSI.  They are SATA.

I believe the problem is Ubuntu as well as Mepis and Fedora do not support either my motherboards (ABIT NF7-S2)  SATA controller (Nvidia Raid MCP) or that they do not support SATA hard drives.

Please help and advise.

Best Regards,
Kevin

---

### Post by razzmatazz on 2005-01-31
Linux kernel (and thus ubuntu) does support SATA drives, and it just shows them as SCSI because they are managed by the SCSI layer.

NVIDIA RAID is actually software RAID (that means it is not a real RAID, only an emulated one), thus you need some tinkering to make it work with linux. (google for "+dmraid +linux")

---


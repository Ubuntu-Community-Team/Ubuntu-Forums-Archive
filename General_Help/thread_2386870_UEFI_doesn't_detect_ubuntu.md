---
title: "UEFI doesn't detect ubuntu"
date: 2018-03-11
forum: General Help
---

### Post by nilq999 on 2018-03-11
Hi! I recently updated the UEFI BIOS to the newest version and I can no longer boot my linux partition. I previously had dual boot managed by grub and everything worked fine. Now I can only boot windows. I've tried setting the boot priority order in the BIOS, but it doesn't even detect the linux partition, as if it didn't existed. Also, I've tried loading the UEFI BOOT MANAGER, but again, it doesn't show my linux partition. What is strange is that different softwares that I've installed tell me different things about this partition. One called EaseUS Partition Master says that the partition is empty. However, another called PartitionGuru says the contrary. I assumed this is because the first software can't manage ext4 partitions correctly. Anyway, what can I do to boot my Ubuntu again?

Thanks in advance.

---

### Post by hrsetrdr on 2018-03-11
Turn off  Secure Boot?  Maybe it got turned back ON, after BIOS update?

---

### Post by nilq999 on 2018-03-11
I tried, but nothing changes. I used to boot both windows and linux with secure boot enabled without any problem.

---

### Post by oldfred on 2018-03-11
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I have multiple settings in UEFI that I must change. And every update to UEFI resets to defaults, so I made a list of the settings I change for my system.
Some now report that Windows major updates may also change settings in UEFI as well as turning on Windows fast start up.

What brand/model system?
Some require special settings.

---


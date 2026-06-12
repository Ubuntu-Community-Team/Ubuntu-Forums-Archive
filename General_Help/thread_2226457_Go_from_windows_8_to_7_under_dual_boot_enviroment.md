---
title: "Go from windows 8 to 7 under dual boot enviroment"
date: 2014-05-27
forum: General Help
---

### Post by maazmahmood on 2014-05-27
Ok, so this is a weird situation. I have my computer dual booted into Ubuntu and Windows 8. They are on separate PHYSICAL hard drives, windows has I think 3 physical hard disks to it, while Linux has 2. Windows drive for this will be called Toshiba, and Linux will be called Seagate. Now, the computer boots to GRUB menu where I select ubuntu or Windows 8. I've tried manually booting to Toshiba and it doesn't work anymore, I feel has something to do with the dual boot. Anyways I want to go back to windows 7 and I was wondering if I unplugged ALL drives but the Toshiba and installed on their would that be a problem with Linux or anything like that? 

Because when booting to Toshiba I get that error, does that mean that both linux AND Windows 8 are on that Seagate drive?

---

### Post by oldfred on 2014-05-27
You have two physical drives, the rest are partitions on the drives.
Windows confuses the issues as it will call a second partition on the first drive d: drive or if second physical drive with both drives having one partition it will also be called a d: drive. 
Linux separates naming for drives like sda, sdb, sdc and then the partitions are the numbers after the drive like sda1, sda2, sdb1 etc.

Best to see details. Post link to BootInfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you disconnect drive it will not modify Linux if it really is on second drive. But if new computer you may have UEFI vs BIOS/CSM boot issues, so post link to BootInfo report.

---

### Post by maazmahmood on 2014-05-27
It's not really a new Computer. It's recognized these drives before. My only concern is that if I installed Windows 7 on Toshiba hard drive with everything unplugged, will it automatically remove Windows 8 or will there still be traces left and I'd have to hunt that down?

---

### Post by oldfred on 2014-05-27
UEFI has been in hardware since about second gen Intel chips. But most Windows 7 systems were installed in BIOS mode even if hardware supported UEFI.
The only issue would be if you changed from one boot mode to another.
If both are BIOS then I would not expect any issues, but have not installed Windows 7 or 8.

 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by maazmahmood on 2014-05-27
I just got home and in the grub menu I realized that it said Windows 8 was on the /dev/sde drive. I did not expect that. I thought it would be in sda, since under gparted the partitioning makes sense.

---

### Post by oldfred on 2014-05-27
With my system the drives are in port order from the SATA ports on the motherboard. But I must have skipped one, so when I plug in a flash drive it is sde, but if I reboot with that flash drive plugged in, it is sdb and all the higher drives are one more.

---


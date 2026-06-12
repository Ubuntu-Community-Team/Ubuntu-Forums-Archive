---
title: "Lost Ubuntu partition when changing format MBR to GPT"
date: 2022-03-06
forum: General Help
---

### Post by cokejho on 2022-03-06
Hello,
I had a DualBoot in my SSD, 1 partition was for Windows 10 and the other one for Ubuntu. I tried to convert the partition format from MBR to GPT using W10 tool AOMEI and it worked successfully at the first view. However, when I rebooted my machine, the grub for dualboot was missing.
I have made a bootable USB with Ubuntu 20.04 and try the installation to open a terminal. I think that my partition with all my data is still there but I don't know how to get her back.

```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print //this printed the current partition table
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start       End         Size        File system  Name  Flags
 1      2048s       1187837s    1185790s    fat32              boot, esp
 2      1187840s    432579597s  431391758s  ntfs               msftdata
 3      432580608s  747522047s  314941440s  ext4               msftdata
 4      747522048s  976771071s  229249024s    

```

I think my Ubuntu partition is the number 3 in the list above. Please, can someone help me_
Thx in advice

---

### Post by cokejho on 2022-03-06
For anyone having the same issue:
Finally, i was able to restore the ubuntu partition, what i did:
1) Clicking option "Verify" in the partition using Gparted program
2) Reinstalling Grub with boot-repair 
It worked for me

---


---
title: "Extended hdd"
date: 2020-05-11
forum: General Help
---

### Post by sadowu on 2020-05-11
I am an Ubuntu 20.04 user, and I recently installed KDE and I really like this OS, I would like to stay on it ... but the problem is that I'm not very good on the partition phase and I would like to delete PARTITION WITH WINDOWS to have much more space on the HDD. I would like my Windows to disappear altogether.

I thought that gParted could be a solution for what I want to do, I never want it to stay, to be a clean hdd.

How to put partitions to have only the KDE?

PS:I want to mention that Windows 10 partition is very infected with  malware and I haven't deleted it ... won't it affect Ubuntu? As I know  that some viruses affect the Kernel, like rootkits, I gave a scan with  rkhunter and it tells me it's okay .. (Probably just paranoia)"

[IMG]https://i.imgur.com/gEXdiPR.png[/IMG]

---

### Post by CelticWarrior on 2020-05-11
No, Windows malware doesn't affect Ubuntu.

Now, from you running system you can delete the Windows partitions but you can't move to the left and resize your Ubuntu root partition to make use of the now unallocated space. You need to boot a live session for this second part.

Be warned that moving and resizing partitions is risky so it's really important that you have backups. 

A better solution, having the proper backups, is to reinstall Kubuntu with the option "erase and install...". This will likely keep the existing EFI partition which is fine and then create a single root partition. A separated swap partition is no longer needed because Ubuntu uses swapfile by default instead.

---

### Post by Impavidus on 2020-05-11
Yes, deleting Widows is trivial; the tricky part is adding the storage space to Ubuntu. You will copy every file from one place on the drive to another, taking ages, so you can just as well backup and reinstall. One big partition for everything will be OK, but it's often a good idea to have one small (about 25GB) partition for the OS and the rest for data.

---

### Post by MoebusNet on 2020-05-13
If all else fails, why not back up all your data to a trusted HDD or cloud service (always a good idea), and do a clean Ubuntu-only install, then import all your data? Should be quite straight-forward. *However*, if it was me, I think what I would do is 1) buy a new HDD/SDD 2) remove & replace the old HDD, keeping it for the unneeded Windows install you've already paid for in case you need it in the future (ie, sell PC).

---


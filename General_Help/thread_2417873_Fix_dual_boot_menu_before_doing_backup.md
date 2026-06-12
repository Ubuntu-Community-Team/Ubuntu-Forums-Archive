---
title: "Fix dual boot menu before doing backup"
date: 2019-04-28
forum: General Help
---

### Post by unoit on 2019-04-28
Hi
I had a dual boot with Linux and Windows. I had problems with my Windows install so I did a new install - then I used Boot-Repair - Recommended Repair to fix the GRUB boot menu - my problem is that my boot menu shows two instances of Windows - one on sda1 and the other on sda2 - it does boot when I choose sda1 option [I have not tried the other one]. Now, I want to do a backup using PING but I am concerned that something may go wrong unless I correct this. Is there a way to easily edit this boot menu? By the way Linux-Ubuntu "Places" shows my Windows install as /dev/sda2. Ubuntu Disks utility shows sda1 as partition 1 System Reserved and sda2 as Filesystem Partition 2 [where Windows is installed]
TIA

---

### Post by oldfred on 2019-04-28
If you are seeing two entries in grub that is ok.

Boot-Repair copies the two main boot files from Windows Boot partition (which you should backup also).
Many users do not know Windows has boot partition and some houseclean it out. Then they cannot boot.
So Boot-Repair does a backup. Windows only boots from primary NTFS partition with boot flag, so only that partition is used by Windows.
But grub2's os-prober does not look at boot flag, but at boot files. And since now in two partitions, it will offer to boot from either.

---

### Post by unoit on 2019-04-28
Hi Old Fred
Thank you for your feedback. I did notice a problem - I tried boot option sda2 - it did boot into Windows - but it shows that Windows is not activated and I have 22 days to do so. When I rebooted using boot option sda1 - it shows that my Windows install is Genuine
Any suggestions?
TIA

---

### Post by oldfred on 2019-04-28
Do not know what Windows has in Boot partition. 
Just having boot files in main, c: drive, was so you could potentially still boot if you made the common mistake of deleting the Boot partition.

---


---
title: "shouldn't a 30gb /home be sufficient?"
date: 2024-09-17
forum: General Help
---

### Post by pjstock on 2024-09-17
My Ubuntu LTE22.04 is setup with a 30gb /home partition, which I thought would be enough to function easily.
But I am down to about 2.9GB free space (looking at PROPERTIES in FILES though in DISKS it is showing as having 4.4gb free. why the difference I don't know)

in any event I was prompted for an automatic upgrade to 24.xx but it failed due to insufficient disk space.

I guess I can try to enlarge /home or delete some stuff.

But should I be so close to having maxed out 30gb?

peter@peter-OptiPlex-990:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           782M  3.4M  779M   1% /run
/dev/sda3        28G   24G  2.7G  90% /
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/sda4       134G   32G   95G  26% /mnt/427bb13e-0609-4207-9628-10860c5d6586
tmpfs           782M  1.7M  781M   1% /run/user/1000
/dev/sdb1       1.9T  1.6T  262G  86% /mnt/usb-Seagate_Expansion_Desk_NA4N2NMT-0:0-part1
peter@peter-OptiPlex-990:~$

---

### Post by ActionParsnip on 2024-09-17
Depends on system use. There is no single answer here. All systems will be different. If /home is part of the root file system and you store lots of pictures...then no. If you have a separate /home file system then maybe.

---

### Post by ActionParsnip on 2024-09-17
From your screenshot /usr/lib is 1/3rd of the file system. If you uninstall packages you don't use (For example LibreOffice is large and if not used, it can be removed to free up space) to free up space on the disk

---

### Post by ActionParsnip on 2024-09-17
You do seem to have a 147Gb Ext4 file system on the disk....is that meant to be used in the Ubuntu setup at all?

---

### Post by oldfred on 2024-09-17
Your 28GB for / (root) now is not large.

I use Kubuntu and keep only hidden (.) files in / and have all my data in separate data partition(s).
I allocated 35GB and do not install any snaps and use about 15GB. Have seen users with 20GB of snaps alone, so now with snaps you need a much larger / partition.

/home also is where data is stored. That varies greatly by user. I do not have much media, music or videos but lots of photos.

---

### Post by hedgehog123 on 2024-09-17
Your /home directory seems not to have a separate partition. Could it be you planned to have sda3 as a separate home partition and sda4 should be the root partition? sda4 is mounted on /mnt/427bb13e-0609-4207-9628-10860c5d6586 and has 95GB free space. So you could backup all data at least from /home and from /mnt/427bb13e-0609-4207-9628-10860c5d6586 and then increase the size of sda3 (and decreasing the size of sda4). Best is to backup all partitions, if something goes wrong also the Windows partition sda2 could be overwritten.
I'm not sure if the tools to change partition size can automatically shift the data from the partition that is decreased so that the data is not lost. But at least you can copy back the data from the backup.

---

### Post by pjstock on 2024-09-18
the Snap directory is the biggest. 12.7GBs
those are installed applications I think.

I unfortunately have never mastered (or understood) partitioning and root and /home assignments or optimal disk space allocations.
it should be easy and logical but I just find the "what goes where" question baffling.
when I do a Ubuntu install it is mostly cross my fingers and pray that it all comes back too life.

I don't know remember where the 147GB Partifion came from
I think it was what was left over on a relatively small HDD after I assigned 30gb to the Ubuntu install.

---

### Post by hedgehog123 on 2024-09-18
Just to give you some more sizes of current Linux distributions, I have a Kubuntu 24.04 with about 30GB used space, Debian 12 with about 15GB including 5GB Flatpak, Fedora 40 without any Snap or Flatpak with about 15GB, all without /home or other data folders, all with KDE Plasma.
But to be fair, the Ubuntu runs on my private development PC, so there are much more programs installed.
So it's plausible that your partition is too small now. Snap is nearly like having an extra virtual machine with a full Linux running in parallel. Since I have enough space, I never thought about that.

For Linux installation, I create one partition for root including home and take all space that is free. Earlier I also tried using separate home partition and after some time I had the same problem you have now, no more space on root though there was much space free on /home.

---

### Post by pjstock on 2024-09-18
In the end I used GParted to reduce the adjacent particiton by 10GB and  increase the 28gb partition to 38GB
that should give me some breathing room

---


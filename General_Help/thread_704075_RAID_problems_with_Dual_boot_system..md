---
title: "RAID problems with Dual boot system."
date: 2008-02-22
forum: General Help
---

### Post by Roguespider13 on 2008-02-22
This might be more of a Windows problem but I still figured this would be the best place to ask.

I built a new system mainly to be used as a Ubuntu file server but when I need more processing power, I have a Windows partition. The system is built with a 160 GB SATA drive (100 GB for WinXP 64 bit, rest offor Ubuntu). The files for the server is stored on a 3 TB array. The array is a RAID 5 (8x500GB, 1 drive is for a hot spare, other is lost with parity bits, so I end up with about 3TB ~ 2750 GB). I paritioned the array so that 2.5 TB was for the files and 250 GB as extra space for the windows parition. The 2.5TB is set up as XFS (either that or ext3, can't remember). the 250 was set up as FAT32 (so I could transfer data between the 2 OSes).

The problem is WinXP sees the entire 2.5 ~2.7 array but as one large drive (rather than partitioned) and it sees it as 100% free. Any one have any idea why I can't see the small 250 GB parition?

---

### Post by fjgaude on 2008-02-22
Please, more information: the raid array is a separate box, a card on a computer, what?

Is the raid hardware or software?

---

### Post by Roguespider13 on 2008-02-22
Specs:

RAID - 3ware 9650SE-8LPML PCI-E card
MOBO - Gigabyte GA-M59SLI-S5
CPU - AMD X2 64 4800+
RAM - 2x1GB OCZ PC6400
HDDs - All Seagate drives

Ubuntu - Feisty Fawn
Windows - Windows XP 64 bit

Just as a side note, when I first built the PC, I had trouble partitioning the drive due to some bug for 64 bit OS in the version of parted that was included with Feisty. I had to use a boot disk of GRML to create the partitions.

---

### Post by fjgaude on 2008-02-22
You have a Linux, Ubuntu driver for the raid card, yes. Or are you using dmraid software?

The 250G partiton in FAT-32... has Windows XP ever seen a partition that big?

You are working in areas that many of us don't go. <smile>

---

### Post by Roguespider13 on 2008-02-22
> **fjgaude said:**
> You have a Linux, Ubuntu driver for the raid card, yes. Or are you using dmraid software?

The 250G partiton in FAT-32... has Windows XP ever seen a partition that big?

You are working in areas that many of us don't go. <smile>

Its a hardware RAID. I do remember the problems with larger than 137GB FAT32 partitions but Windows should at least be able to see the partition.

---

### Post by ZeroZ400 on 2008-02-22
Whats the output of
```
cat /etc/fstab
```

---

### Post by fjgaude on 2008-02-22
And what does gparted look like for that drive?

```
sudo apt-get install gparted
```

In case you don't have it on your boot-up system.

---


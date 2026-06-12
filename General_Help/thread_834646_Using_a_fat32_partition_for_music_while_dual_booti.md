---
title: "Using a fat32 partition for music while dual booting"
date: 2008-06-19
forum: General Help
---

### Post by spark29 on 2008-06-19
I just got ubuntu running perfectly in dual boot with vista on my new laptop. I prefer using ubuntu for everything besides games...but i would like to be able to play music on both os's. Originally the laptop came formatted with 2 partitions split down the middle for the c drive in vista and then a blank data partition. I believe the data partition is ntfs. Would it be possible to just reformat that partition as fat32 using fdisk, then save all my music to it, and let the players like itunes and whatever ubuntu uses open from there? I would have already tried this, but it seems that when i enter fdisk -l to view my partitions, nothing happens. Help.

Thanks in advance.

---

### Post by petzworld999 on 2008-06-19
When I was dual-booting Ubuntu and Vista, I was able to play music off of my Windows partition, which was formatted as NTFS, with no problems. The idea you have proposed should work. As for the fdisk -l problem, try running it as root with sudo fdisk -l. That should bring up information.

---

### Post by VMC on 2008-06-19
Output these

```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
```

---


---
title: "Help moving data from live disk"
date: 2008-01-14
forum: General Help
---

### Post by JaggedOne on 2008-01-14
Windows XP on my girlfriends PC recently died and stopped booting. I talked her into letting me wipe the drive and install XP and ubuntu dual booted. Before I do that I want to copy the old husk of her previous XP boot to my back up drive so we could pick off files she might want later. The only working experiment I can get on the machine is a live disk. Even when I try and copy files in the command like with sudo, it says I do not have permission. How do I get permission to move files between two separate disks in a live CD environment?

---

### Post by NilsE on 2008-01-14
Have you tried starting Nautilus in a terminal with gksudo

gksudo nautilus

---

### Post by perixx on 2008-01-14
> Nautilus in a terminal with gksudo 
If I may add here - in case he uses Xubuntu:
```
ALT+F2 --> gksudo Thunar
```

Might be, that NTFS-functionality on the live-CD is missing and he needs to install 'ntfs-3g' for full read/write access with Synaptic first, then to mount the partition (needs to be done in the first place via Nautilus / Thunar or CLI anyway, if it's not done already)...

If the user-ownership is the problem - and since the system is trashed anyway - he might claim ownership over the files to recover with:
```
sudo chown [USERNAME - possibly 'root' on Live-CD] /media/[hda1?/sda1? - XP-partition]/.../[somefolder]/*
``` - this will change permission of the files in [somefolder] to [USERNAME] (maybe 'root' with live-CD). 
The problem: using 'root' will possibly prevent the usage of the files as non-root under Ubuntu (so changing ownership twice might be neccessary), and changing ownership may result in access-problems under XP as well - I'm not sure.

perixx

---


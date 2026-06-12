---
title: "Extra devices showing up that aren't mountable anyway"
date: 2013-11-30
forum: General Help
---

### Post by dannyboy79 on 2013-11-30
I recently changed my fstab to not mount some network shares upon start up but instead added a script to be run once the desktop is up and for some reason these extra icons were added to the devices section of thunar. I am using Xubuntu 12.04.3, XFCE 4.10. Here's what I am talking about 
[IMG]https://lh3.googleusercontent.com/-sGP0RdG9wPA/Upm7K04momI/AAAAAAAACRg/U_hbfDO_PSs/s640/image_2013-11-30_04%253A16.jpg[/IMG]
here's the fstab entry for 1 of the devices
```
192.168.0.5:/media/WDMBWE1TB /media/WDMBWE1TB nfs users,noauto,rsize=32768,wsize=32768,intr,hard	0	0
```
i get an error when I click on it that it can't be mounted because it's busy. i don't want them there, how can I get rid of them? it also doesn't make sense that they show up under places and devices. its also weird that NFS and CIFS shares are showing up within places, shouldn't those be in the network section?

---

### Post by Bucky Ball on 2013-11-30
Remove the appropriate lines from fstab and delete the local mountpoint in /mnt or /media or where you have them. Reboot.

PS: You can also just put a hash mark (#) in front of the lines you don't want in fstab. They will then be ignored. If you want to use them again in the future just remove the hash mark.

---

### Post by dannyboy79 on 2013-11-30
in order for my script to mount the network shares to work don't those entries need to be present in the fstab? Here's the script
```
#!/bin/bash
mount /media/500gb1
mount /media/WDMBWE1TB
mount /media/fat32
mount /var/lib/mythtv
mount /mnt/circle

```

---


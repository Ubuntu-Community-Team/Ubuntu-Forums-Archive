---
title: "Want to use 2nd hard drive just for storage"
date: 2007-01-05
forum: General Help
---

### Post by abyss6 on 2007-01-05
I have a second hard drive that I just installed that I want to use just as a storage drive so that I don't have to back up all of my files when I format and reinstall.  During the installation process, I formatted it using ReiserFS.  When it came time to select a mount point for it, there were several options (/, /boot, /var, /usr), but nothing that said just "storage" to me.  What is the best option for this so when I want to format and reinstall again, I can leave that drive alone and not have to worry about it?

Hope that isn't too confusing.  TIA.

---

### Post by kingmonkey on 2007-01-05
you can create any mountpoint you wish such as /data /storage /mnt/hdb1 whatever

The best mount point imo however would be /home but please read [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) from the title "Using the new partition" carefully first.

---

### Post by abyss6 on 2007-01-05
Thanks.  One thing I've noticed in this new install (and it may or may not be related), is that the new hard drive does not show up in "Computer", and there are two floppy short cuts - one for the floppy drive and another that shows the capacity as 19 gigs.  I'm not at this computer at the moment, but IIRC, my swap partition was set at 21 gigs.

Any idea what this is?

---

### Post by Cholito on 2007-01-05
Hi! it's not in "Computer" as it doesn't have a mount point ;) first create a mount point for that hd. I use /home for my data (using a partition in the same sda thou)
Saludos
Alejandro Matos

---

### Post by Crimguy on 2007-01-05
I think someone needs to point out that you need to edit your /etc/fstab file to have the drive mount at startup.  You have to format and partition it as well.  Install gparted for the latter, use the command sudo gedit /etc/fstab for the former.

Sorry if I'm being pathetically obvious ;-D

---

### Post by mcduck on 2007-01-05
> **abyss6 said:**
> I'm not at this computer at the moment, but IIRC, my swap partition was set at 21 gigs.

21 GB is pretty much for swap. The recommendation is 1.5 - 2 times your RAM..

---


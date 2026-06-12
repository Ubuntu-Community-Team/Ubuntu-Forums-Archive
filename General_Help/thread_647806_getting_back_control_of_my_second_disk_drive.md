---
title: "getting back control of my second disk drive"
date: 2007-12-22
forum: General Help
---

### Post by billcharv3 on 2007-12-22
I just used sudo to do a gedit of fstab to get my second hard drive to mount at my boot up.  I was very happy...now I need to change the owner from root to me...I used gksudo to open nautilus and tried to change the owner from root to me, but it automatically and instantly changes it back...what can I do to achieve this..??? Please be specific, as I am a new user...

---

### Post by taurus on 2007-12-22
What is the filesystem of that second harddrive and how do you mount it in /etc/fstab?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by billcharv3 on 2007-12-22
I added a line to mount it, and it does it...
I entered:
/dev/sdb1  media/disk2   ntfs  rw, user -------more stuff ----
Yet it is ntfs...is that an issue?

---

### Post by taurus on 2007-12-22
Why don't you use ntfs-3g to mount it?

```
sudo apt-get update
sudo apt-get install ntfs-3g[code]
Then, modify your /etc/fstab and make it look like this.

[code]/dev/sdb1   /media/disk2   ntfs-3g   defaults   0   0
```
Reboot and you should be able to read and write to it, /media/disk2.

---

### Post by billcharv3 on 2007-12-22
Just tried it and rebooted.....results are in...
THAT DID IT...!  you are the best....
Hey, another thing,,,since you are so helpful...
I always get errors about compiz,,,I think it is because my old NVidia card only has 64mb Ram and is not 3d compliant... is that true>?
MANY THANKS..Taurus is #1

---

### Post by taurus on 2007-12-22
What model is that nVidia card?  I have eVGA GeForce 5600 in the office and XFX GeForce 6800 at home so compiz is no problem at all.

---

### Post by billcharv3 on 2007-12-22
Nvidia 
NV5M64 [Riva TNT2 Modle 64/Model 64 Pro]
PCI

---

### Post by taurus on 2007-12-22
Which nVidia driver did you install:  nvidia-glx or nvidia-glx-new?  Maybe you need the nvidia-glx instead of the nvidia-gfx-new.

---


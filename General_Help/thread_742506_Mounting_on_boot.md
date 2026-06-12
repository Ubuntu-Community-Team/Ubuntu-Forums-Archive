---
title: "Mounting on boot"
date: 2008-04-01
forum: General Help
---

### Post by cuulcars on 2008-04-01
I've been wondering... How do you make drives mount on startup? Its becoming a nuisance having to mount my Windows volume (which has all my music on it) manually after every start-up so... How's it done?

---

### Post by Slushdoot on 2008-04-01
You add an entry in /etc/fstab that tells it how to mount the drive so it works.

Check this out for more info: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Patb on 2008-04-01
Cuulcars.  Take care when editing your /etc/fstab file.  Do not edit any of the existing lines unless you are quite confident.  For details and syntax, man fstab.  

The device designation of your music drive should be given by:
```
sudo fdisk -l
```

[Here is one helpful link]("http://ubuntuforums.org/showthread.php?t=595738") and a search for fstab will no doubt reveal others.  

You will need to create the folder where you want the drive mounted, if it doesn't already exist.  

Good luck.  Cheers, Pat.

---


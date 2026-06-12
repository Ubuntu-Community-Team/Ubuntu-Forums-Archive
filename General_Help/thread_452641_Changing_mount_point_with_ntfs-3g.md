---
title: "Changing mount point with ntfs-3g"
date: 2007-05-23
forum: General Help
---

### Post by GMaq on 2007-05-23
Hello,
    I am dual-booting XP and Feisty, and have a partition for Feisty (ext2) a partition for XP (ntfs) and a common work partition for both Os's(ntfs). Everything is working wonderfully except that I set the mount point as /media/Work Drive/ and many applications and anything in the terminal don't like the "white space" between "Work" and "Drive" so I want to change the name in the mount point. I am using the NTFS Configuration Tool and it utilizesthe drives perfectly but doesn't allow me to change the mount point. I am still a beginner with terminal command lines, so any guidance would be appreciated.

---

### Post by taurus on 2007-05-23
If you mount it through /etc/fstab, you can just edit it

```
gksudo gedit /etc/fstab
```
and replace it with the new mount point.  Then, save it and create the new mount point so it can mount to it, assuming the new mount point is called /media/Drive.

```
sudo mkdir /media/Drive
```
Then, reboot.

---

### Post by GMaq on 2007-05-23
taurus,
     Thank you very much that did the trick, One more question though. In my /media folder is an empty folder "Work Drive" that of course I cannot delete via the file manager. What is the command to remove this obsolete folder from the terminal?? Thanks again for your time!

---

### Post by nothing_happened on 2008-03-20
```
sudo rm /media/Work\ Drive 
```
that should do the trick after you type in your password, or if you are too lazy to type out the \ there

```
sudo rm "/media/Work Drive" 
```

---


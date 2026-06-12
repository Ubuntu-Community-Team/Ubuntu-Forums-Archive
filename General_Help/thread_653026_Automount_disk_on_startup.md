---
title: "Automount disk on startup"
date: 2007-12-29
forum: General Help
---

### Post by Dark Aspect on 2007-12-29
How do I make it where I can mount my secondary 40 GB internal drive (NTFS) on the Ubuntu start up so I don't have to do it under gnome.I tried pmount but it only works with external drives,is there a way to do this with fdisk?

Better yet I wanted to do this because I have a shared folder under virtual box going to the 40 GB hard disk so if there is a way to mount the drive automatically under Vbox that would work too.

---

### Post by icheyne on 2007-12-29
[http://doc.gwos.org/doku.php/doc:hardware:fstab](http://doc.gwos.org/doku.php/doc:hardware:fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by taurus on 2007-12-29
You can add an entry in /etc/fstab for your ntfs partition so that it would be mounted automatically each time you boot Ubuntu.  

Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by FuturePilot on 2007-12-29
Install ntfs-config.
```
sudo apt-get install ntfs-config
```
Then it will be under Applications>System Tools

---


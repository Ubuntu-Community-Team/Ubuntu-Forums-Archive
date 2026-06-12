---
title: "Renaming ext3 partition(s)"
date: 2006-11-19
forum: General Help
---

### Post by indytim on 2006-11-19
I want to rename a couple of my mounted partitions to something more meaningful.  Would appreciate comments back on the following approach:

Present mounted partition name : sdb4 (it's my second sata drive)
New Name : LxBackup

Option 1:

1. Rename the /media/sdb4 -> /media/LxBackup
2. Edit fstab and change the named partition from sdb4 to LxBackup

Option 2 :

1.  Create a new folder in /media called LxBackup
2.  Add a new line entry in fstab to reflect the /media/LxMedia as the mount point for sdb4

Expert comments appreciated on the above.

Thanks,

IndyTim

---

### Post by temcat on 2006-11-19
There's also another option - use tune2fs program to change volume label of the disk:

```
sudo tune2fs -L NewLabel /dev/sdb4
```

The label can be maximum 16 characters long, the rest will be truncated. The tune2fs program is a part of the e2fsprogs package (in case you don't have that installed). AFAIR you'll have to reboot for the system to use the new label.

---

### Post by indytim on 2006-11-19
The tune2fs worked well :D .

Many Thanks,

IndyTim

---

### Post by TLE on 2006-11-19
If you don't use temcat's suggestion. I definitely think it should be options 2. BTW there is one more little issue here. For the things that are mounted in /media/ there's created a shortcut on the desktop and in the "My machine" folder. And the name of that shortcut has nothing to do with the mount point, but is the actual name of the partition. So if it is the names of those shortcuts you want to change I think you have to change the name of the partition. Maybe with the tool temcat suggested.

---


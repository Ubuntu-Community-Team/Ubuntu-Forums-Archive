---
title: "fsck problem- not working right on boot"
date: 2007-01-29
forum: General Help
---

### Post by mysticrider92 on 2007-01-29
I re-installed Ubuntu Edgy on my computer after installing Windows XP and used a backup I had made to get everything back to how it was before. Now when I boot Ubuntu, it goes through the usual process, but when it checks the file system, it gives this error:
> fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=f360426c-38bb-4993-9083-08055bc13b5e'

and gives me a rescue terminal. From there, I can tell it exit and boot into the desktop and everything seems fine. I also checked gparted to see what it said about my partitions, and it says the the mount point for /dev/sda2 (ext3 for Ubuntu) wasn't found. Can anyone think of a solution? It isn't a major problem, but I don't think it should be doing this. My partitions are /dev/sda1 for Win XP, /dev/sda2 for Ubuntu, and /dev/sda3 for swap. If this is in the wrong place or already asked, sorry, I didn't see anything about it.

---

### Post by p!=f on 2007-01-29
> **mysticrider92 said:**
> I re-installed Ubuntu Edgy on my computer after installing Windows XP and used a backup I had made to get everything back to how it was before. Now when I boot Ubuntu, it goes through the usual process, but when it checks the file system, it gives this error:

and gives me a rescue terminal. From there, I can tell it exit and boot into the desktop and everything seems fine. I also checked gparted to see what it said about my partitions, and it says the the mount point for /dev/sda2 (ext3 for Ubuntu) wasn't found. Can anyone think of a solution? It isn't a major problem, but I don't think it should be doing this. My partitions are /dev/sda1 for Win XP, /dev/sda2 for Ubuntu, and /dev/sda3 for swap. If this is in the wrong place or already asked, sorry, I didn't see anything about it.
By reinstalling edgy your UUID for /dev/sda2 has changed. Type
```

sudo vol_id -u /dev/sda2

```
(you need vol_id package)
and edit your /etc/fstab.

---

### Post by mysticrider92 on 2007-01-30
There seem to be some good and bad things about having so much control over the computer. I have now gotten my partitions completely confused, and will probably end up completely destroying this install. I think I will reinstall it and not restore the etc folder. Thanks for the help.

[edit] Mixing configuration files in /etc between systems/installs is not recommended. :D

---

### Post by godfree2 on 2007-02-01
same problem here except I did not reinstall,
I just rebooted one day after using winME.
boom fsck fails; seems the UUID is wrong.
I did nothing to change the partitions or resize them.

no sign of the vol_id
program mentioned.
where is it?

why do linux distros continue to shoot themselves in the foot (and users in the head)  by altering boot up procedures without failsafes or permission?
=9(***)9

---

### Post by p!=f on 2007-02-01
> **godfree2 said:**
> 
no sign of the vol_id
program mentioned.
where is it?

Seems like it's called volumeid now.
> 
apt-cache show volumeid


---

### Post by jerrykenny on 2007-02-01
In order to verify your partition table looks like what-you-think-it-is, you can boot into any "live" linux distro, open a terminal, and <cfdisk /dev/sda>  

Or use a windows 98 recovery floppy, then fdisk


My own Sata drive simply wont work properly with linux unless its jumpered for the lower-than-default transferr rates (cant remember what they are)

Performance is still very respectable, . . . .


You may then need to adjust your /etc/fstab  file, and add the correct fstab entry for the root filesystem.

---


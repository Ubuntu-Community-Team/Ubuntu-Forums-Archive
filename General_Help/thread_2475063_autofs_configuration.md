---
title: "autofs configuration"
date: 2022-05-15
forum: General Help
---

### Post by rsteinmetz70112 on 2022-05-15
I decided to try out autofs because I had a failure where my remote backup because the external USB drive was not mounted, even though it was working in fstab.

I installed autofs and confirmed it was working. I added disk labels to all of my partitions and set up an auto.direct file containing these two lines;

```
/backups        -fstype=ext4            :/dev/disk/by-label/backups
/ntfs-backups   -fstype=ntfs-3g         :/dev/disk/by-label/ntfs-backups
```

At first it seemed to work but upon reboot the ntfs file system will not mount. I get an error that it does not exist. The ext4 filesystem works as expected.

Both filesystems do get mounted under /media/user/LABEL.

---

### Post by TheFu on 2022-05-16
> **rsteinmetz70112 said:**
> I decided to try out autofs because I had a failure where my remote backup because the external USB drive was not mounted, even though it was working in fstab.

I installed autofs and confirmed it was working. I added disk labels to all of my partitions and set up an auto.direct file containing these two lines;

```
/backups        -fstype=ext4            :/dev/disk/by-label/backups
/ntfs-backups   -fstype=ntfs-3g         :/dev/disk/by-label/ntfs-backups
```

At first it seemed to work but upon reboot the ntfs file system will not mount. I get an error that it does not exist. The ext4 filesystem works as expected.

Both filesystems do get mounted under /media/user/LABEL.

You have competing mount tools.  Disable the tool that is mounting stuff under /media.
My autofs mount for ntfs line looks like this:
```
/misc/250G    -nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002    LABEL=250G
```

The auto.master file looks like this, which points at the auto.misc (contents above):
```
/-      /etc/auto.misc --timeout=60 --ghost
```

The **/-** is critical.  See how I use the LABEL=?

---

### Post by rsteinmetz70112 on 2022-05-16
Thanks. 

I'll need to figure out how to disable the mount in /media. Ideally I'd like to keep it automatically mounting any general USB devices like a thumb drive or something. 
It looks like the most promising way is a special udev rule tied to the specific device, but I guess I'll need to figure out udev rules.
Perhaps the key to the auto mounting is to change the fstype to just plain ntfs, although I found examples using the fstype I used.

---

### Post by TheFu on 2022-05-16
In the file manager is usually where the /media mount checkbox is.  I usually just purge udisk or udisk2 from my systems. I consider automatic mounts to be extremely dangerous, since there are multiple attack vectors against every platform, including Linux, that use this mode.  The power to mount, is the power to destroy.  Always remember that.

Even if you disable automatic mounts, IME, we can still manually click on a device to mount it.  That isn't too much hardship.

Autofs using LABELs gives us the convenience of easy USB mounting devices that we know about, but not mounting 'unknown' devices automatically.  I seldom touch USB storage that isn't mine and LABEL'ed.  Around 2011, I was running a Linux InstallFest at the local University.  It was my first time and I really didn't prepare too well.  I brought a single USB3 Flash drive with 6 different distro ISO files.  There were less than 20 people attending, so I just passed that flash drive around for people to copy the ISOs and virtualbox off.  By the time that flash drive went around the room and was returned to me, it had 3 nasty viruses on it.

As for the fstype - ntfs == ntfs-3g  They are the same.  I'm in favor of using the fewest characters, that achieve the desired goal, though you wouldn't guess that based on my autofs line. ;)

---

### Post by #&amp;thj^% on 2022-05-16
> **TheFu said:**
> The power to mount, is the power to destroy.  Always remember that.



Words to Live by.

---


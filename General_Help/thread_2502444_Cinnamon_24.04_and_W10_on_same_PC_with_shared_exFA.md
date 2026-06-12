---
title: "Cinnamon 24.04 and W10 on same PC with shared exFAT documents drive."
date: 2024-11-14
forum: General Help
---

### Post by tedman2 on 2024-11-14
I have a PC with my GoTo drive having Ubuntu Cinnamon 24.04 and another drive with W10 on it. 
In October 2025 I will have to pull the internet connection on the W10 drive.
Hence my conversion to Ubuntu.

These are separate push button ON/OFF drives.
Another drive of the same type has a exFAT documents drive that is always on, no matter if I am using Cinnamon or W10.

The problems that I am having from the Ubuntu side are things like permissions, ownership, read and write etc.
These issues seem to come and go ?
I have Libre Office on both drives with Libra set to be the default for text files etc.
That seems to be working OK. Well - at the moment anyway.

Having tried and failed with other formats, internet research seems to suggest that the best all round solution for my need is the exFAT format.
Being able to use the same Documents drive for the two operating systems would be extremely useful.

Can anyone advise me as to what it is that I am not doing ?

---

### Post by grahammechanical on 2024-11-15
From the little bit I have read Ubuntu should be able to read/write to ExFAT file systems by default in Ubuntu versions from Ubuntu 20.10 and newer. This earlier thread on Ubuntu Forums might be useful to you. Note the second post by @oldfred

[https://ubuntuforums.org/showthread.php?t=2498861](https://ubuntuforums.org/showthread.php?t=2498861)

> Having tried and failed with other formats, internet research seems to  suggest that the best all round solution for my need is the exFAT  format.

That may not be strictly true for large drives.

Regards

---

### Post by yancek on 2024-11-15
Linux permissions such as owner:group, read, write, execute are not used or understood by windows filesystems so you need to use other methods.  If you have this drive always attached, you should have an entry in the /etc/fstab for that drive and partition and use umask, fmask and dmask.  You can do an online search for mounting windows filesystems such as xfat on Ubuntu and get a lot of results.

If you are booting into  windows with the drive attached, the default is to have hibernation always on and if you boot Ubuntu without turning hibernation off in windows, Ubuntu will not mount the drive and it will not be accessible from Ubuntu.  You should get a message when you try to mount a windows filesystem that is hibernated.  There are instructions at the microsoft site explaining how to turn hibernastion on/off.

---

### Post by TheFu on 2024-11-15
Ownership, groups, and permissions for foreign file systems (NTFS, FAT32, exFAT) can only be provided to Linux as the file system is mounted.  That means you need to set them as mount options *somehow*.

There are multiple ways to mount all file systems, but for permanent storage that is always connected, the best, easiest way, to deal with it once and for all, is through adding 1 line to your /etc/fstab file per file system.

There are 6 fields in the fstab file.  **man fstab** will explain each, if you care to look them up. You should.
Also, foreign file systems should only be used for pure data files, not programs, not scripts, not devices, just data. Nothing else.
 
So, a sample line for your fstab file is:
```
LABEL=[COLOR="#FF0000"]what-ever-label-you-set[/COLOR]    [COLOR="#FF0000"]/media/data[/COLOR]    exfat   uid=[COLOR="#FF0000"]1000[/COLOR],gid=[COLOR="#FF0000"]1000[/COLOR],fmask=0002,dmask=0002,nofail,noatime,nodev,windows_names,nosuid,asyncerrors=remount-ro    0     0
```

That must be on 1 line. If your editor wraps it, that's bad. 
You need to set the **label** on the file system using something like **gparted**. No spaces allowed for simplicity.
The mount location, /media/data, is a directory and needs to pre-exist. 

After any changes to the fstab (since systemd was forced onto us), requires running a command to have systemd re-read the file.
```
sudo systemctl daemon-reload
```
To mount it after that, run
```
sudo mount -a
```

Now just visit  /media/data using any method you like to see the files there.
For the uid and gid I made some assumptions that the userid is the first one created on the system.  If that isn't the situation, run the **id** command and post the results back here.
If you need more than 1 user to have more than read-access to the files, things are a little more complex to do it well, but it isn't hard.

---


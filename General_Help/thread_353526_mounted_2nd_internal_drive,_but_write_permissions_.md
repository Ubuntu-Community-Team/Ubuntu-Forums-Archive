---
title: "mounted 2nd internal drive, but write permissions wrong"
date: 2007-02-04
forum: General Help
---

### Post by gregconquest on 2007-02-04
I'm trying to mount an internal SATA FAT32 drive, but I'm not getting the correct write permissions. This is what I have tried in fstab:

```
# FAT32 drive for common Windows/Linux application data
/dev/sdb1 /media/SATA320FAT32 defaults 0 0
```
and then
```
# FAT32 drive for common Windows/Linux application data
/dev/sdb1 /media/SATA320FAT32 vfat rw,suid,dev,exec,auto,user,async 0 0
```
 
Under either of the above two fstab entries, I cannot copy files to that drive. I can see it mounted successfully, and I can copy files from it, but no writing is allowed.

All the mount examples for fstab that I can find have lists of mount options, which I have read, and they have a *few* examples of how drives are mounted, but they're all for floppies, CDROMs, and external USB drives:mad:  There are no examples of second hdd's that get auto-mounted at boot. I can't extrapolate what mount options I need from these other drive types.

Can someone help me, please? My ultimate goal is to use a common profile for Thunderbird for both Windows and kubuntu, but it won't work now, and without the correct write permissions, I can't isolate the problem to Thunderbird:
[http://www.ubuntuforums.org/showthread.php?t=352833]("http://www.ubuntuforums.org/showthread.php?t=352833")

 Thanks,
Greg Conquest

---

### Post by taurus on 2007-02-04
```

/dev/sdb1   /media/SATA320FAT32  vfat   iocharset=utf8,umask=000   0   0

```

---

### Post by gregconquest on 2007-02-04
Yeah! taurus. It worked :)  I did the following:
1) From Konsole (or other terminal)
```
kdesu kate  /etc/fstab
``` (for kde / kubuntu; for gnome / ubuntu -- gksudo gedit /etc/fstab) (correct me if I'm wrong:KS )

2) I altered the previous relevant fstab lines (mentioned at the beginning of this thread) to this:
```
# FAT32 drive for common Windows/Linux application data
/dev/sdb1 /media/SATA320FAT32 vfat iocharset=utf8,umask=000 0 0
```
The first line is a comment (# comment . . .)

3) Save/close/exit all settings, files
4) Reboot

I can now use Konqueror to create/move files on the drive in question. The page below spells this all out in more detail:

[http://lgacorp.wordpress.com/tag/ubuntu-linux/](http://lgacorp.wordpress.com/tag/ubuntu-linux/)
under the entry:
   Hard Disk Drive
   December 12th, 2005 · No Comments
   Ubuntu Linux commands
   Mounting HDD’s fixed or USB / NTFS or Fat32,
   editiing for automount on reboots.

I still don't know why "iocharset=utf8,umask=000 0 0" works, and may be the best choice, but is not generally mentioned in the most easily found Q&A's dealing with this issue. Check the keywords:
fstab mount options
and you won't find this answer. Till now, perhaps. I'll post this message text in the Windows/Linux Thunderbird common profile and data [http://www.ubuntuforums.org/showthread.php?t=352833]("http://www.ubuntuforums.org/showthread.php?t=352833")

:guitar: 
Greg Conquest

---


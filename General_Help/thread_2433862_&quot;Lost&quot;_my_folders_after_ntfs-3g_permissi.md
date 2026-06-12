---
title: "&quot;Lost&quot; my folders after ntfs-3g permission change"
date: 2019-12-26
forum: General Help
---

### Post by girardkirth on 2019-12-26
Newbie here, I was wondering if you guys could help me?  I switched over from windows to Kbuntu a couple of  weeks ago and all my other internal hard drives are NTFS.  They mounted fine but I cannot delete, move, create etc. 

 So after searching I tried a: [FONT=monospace][COLOR=#000000]sudo ntfs-3g -o ro,uid=1000 /dev/sdb1 /media/jerett. 

After that all my drives are saying "The file or folder /media/jerett/(bunch of numbers) does not exist. Can anybody help me figure out what I did here exactly and reverse it? Any help would be appreciated, as I have tried to search for a solution but I'm not 100% sure what I did.[/COLOR][/FONT]

---

### Post by CelticWarrior on 2019-12-27
Apparently you forced mounting it 'read only' (the opposite of what you were trying to do?).

The problem likely was 'dirty' partitions, either due to the Fast Startup feature in all Windows 8 and newer that should have been disabled before removing Windows, or they had logical errors already that were made worse by that command.

---

### Post by Impavidus on 2019-12-27
Whenever you use the file manager to mount some partition, it creates a directory to use as a mountpoint at /media/username/some-numbers. But you manually mounted a partition read-only at /media/username. After you did so, it was impossible to create the empty directories there to use as a mountpoint for other partitions.

If your ntsf filesystem is unclean, it will always mount read-only. Linux isn't very good at cleaning up Windows filesystems, so use Windows for that. If you no longer have Windows on that computer, stop using ntfs partitions.

---

### Post by CelticWarrior on 2019-12-27
> **Impavidus said:**
> If your ntsf filesystem is unclean, it will always mount read-only. Linux isn't very good at cleaning up Windows filesystems, so use Windows for that. If you no longer have Windows on that computer, stop using ntfs partitions.

My thoughts exactly.

Knowing this, if you have Windows available (8 or newer) in another computer, please use to it check for errors and correct them if necessary by connecting the drive to that PC, then backup to a different drive and lastly format it as EXT4.

---

### Post by TheFu on 2019-12-28
If you mounted using the fstab, then by default, root:root will be the owner and group.  Permissions for all files and directories are set using mount options for non-Linux file systems like NTFS, exFAT and FAT32.  Also, some performance enhancing options are only available in the fstab mounts, not through a GUI, so if you are moving lots of files to/from the NTFS partition, you will want to use those options.  There are lots and lots of examples of NTFS mount lines in these forums for the fstab.  Search and you will find.  I'd say look for "big_writes", since that is an important mount option.

However, if you insist on point-n-click access to the disk, which will mount it using gvfs or gio, performance will suck, but the owner and group will be set to the userid/groupid of the account doing the point-n-click.

I'm making lots of assumptions which may not be true.  Each of the replies above are making some assumptions.

This isn't not valid and using sdb1 is a poor choice, since the device can change with each boot.
```
sudo ntfs-3g -o **ro**,uid=1000 /dev/sdb1 /media/jerett
```
That specifically asked for a read-only mount. Nothing you will do will allow any userid to modify anything on that partition. NOTHING.

Something better would be 
```
sudo mkdir /media/extern-disk
sudo mount -t ntfs -o nodev,windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002  /dev/disk/by-uuid/......  /media/extern-disk
# and when you are done, un-mount it with
sudo umount /media/extern-disk
```
You can use those options in the fstab, btw.

The UUID will need to be determined.  **blkid** command will show it.

---

### Post by vanadium on 2019-12-29
To keep things simple, indeed, do not perform any command line mount at all. Instead, make sure your partitions are "clean". Then they will mount automatically and correctly when clicking them in the file manager.

If a partition is *not* clean, have it checked and repaired under MS-Windows. Also make sure they are correctly closed when you use them in Windows. They will *not* be correctly closed upon shutting down MS Windows if "faststart" is enabled, or if you hibernate Windows. If you want them to be correctly closed when you close Windows , disable "faststart" and fully shut down Windows before attempting use under Linux.

If you do not have MS-Windows available, indeed do not use ntfs for critical data storage. Linux has basic checking tools for ntfs, but not to the level of the tools of MS Windows.

---


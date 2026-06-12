---
title: "NTFS mounting - errors options"
date: 2013-05-02
forum: General Help
---

### Post by TheGrave on 2013-05-02
Hello,  I'm having hard times understanding the errors options of the mount command when used in conjunction with the ntfs-3g driver. For years I've been having problems with this driver leaving the filesystem in bad state. Whenever this happens on the next mount I get an error message similar to "Fixing filesystem problems" which creates even a bigger mess. After the ntfsprogs and NTFS-3G projects have merged I assume the mount command is calling ntfsfix to clean up the mess, is that right?  Now next thing I don't quite understand is  the errors options of the mount command. According to the manual they are not listed under the usable options for the ntfs-3g driver but the command accepts them. I started mounting with errors=remount-ro. Is this going to save my ass (read: mount as read-only instead of calling ntfsfix) in case the NTFS filesystem is messed up and the chkdsk flag is set on it?  Cheers

---

### Post by Mark Phelps on 2013-05-03
Unfortunately, ntfsfix only fixes the most basic of NTFS problems.  IT is not a substitute for Windows CHKDSK as basically, what it does, is flag the partition as "dirty" so when Windows next sees it, it will automatically run CHKDSK against it.

Linux automatically forces the mount to be read-only if it detects problems in the filesystem.  As long as you are only READING the filesystem, that should not cause further problems.

If you have to resort to the FORCE option to get the filesystem to mount, that is likely to damage it even further.

In contrast, I've been using the ntfs-3g option to mount NTFS partitions for years (starting back when you had to install ntfs-3g manually) and have not encountered any problems.  But then, I only mount Windows OS partitions read-only, and even then, only when needed (do NOT have them in the fstab file).  I do regularly mount NTFS DATA partitions read-write, and since I take special card to "safely remove" them, I've not run into problems there, either.

Sorry to say, but if you are regularly experiencing NTFS problems, could be that the hard disk containing those partitions is failing.  That's been the case when I encountered them in rare situations.

---

### Post by TheGrave on 2013-05-03
That's why I completely purged ntfsfix from my system though a better idea hit me later - keep it with 000 permissions and set +i attribute so that it cannot be overwritten after an ntfs-3g package upgrade. This tool is doing more harm than good so it must stay disabled.  Anyway, what I want to make sure of is that either with or without errors=remount-ro option I'm keeping the NTFS filesystem safe. If there is an issue I can fire up a WIndows VM and fix it (yeah, by the way this is an iSCSI drive). So, can anyone tell whether this options works with ntfs-3g driver and how exactly does it work - preventing rw mounting of corrupted filesystem + disabling calling of ntfsfix on errors or something else?  Drive's SMART data looks good, no bad sectors either so drive is certainly in good health. It's the ntfs-3g driver that messes it up. As I don't use Windows anymore (except on a VM) I plan to convert this filesystem to EXT4, ZFS, or btrfs later but this will take a while.

---

### Post by VideoRoy on 2013-05-03
I am not sure I understand your problem completely but I was having similar corruption problems due to NTFS partitions getting auto-mounted a few years back. I spent a lot of time trying to learn / resolve.  Of course mine are local not iSCSI.

What I did and do on each new install now is hide the partitions in FSTAB then create symbolic links to just the directories I need to access.  Maybe not exactly what you want to do but maybe my lines from FSTAB will give you some ideas.

> # Hide Some Windows Partitions# Reserved Win7 Boot
/dev/sda1 /Windows/sda1 ntfs-3g defaults,umask=777 0 0


# Win7 C: but create symbolic link later
/dev/sda2 /Windows/sda2 ntfs-3g defaults,uid=1000,dmask=027,fmask=137,locale=en_US.utf8 0 0


#Example of a FAT partition HP_Tools
/dev/sda3 /Windows/sda3 vfat defaults,umask=777 0 0




Then in a Win7Dir folder or where ever you want create a symbolic link.

> ln -s /Windows/sda2/Users/Admin/Documents



Note I create a "Windows" directory off of "/" for the mount point in FSTAB

---


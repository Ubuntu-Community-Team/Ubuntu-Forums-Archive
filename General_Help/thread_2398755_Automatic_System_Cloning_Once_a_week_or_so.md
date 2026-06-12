---
title: "Automatic System Cloning Once a week or so?"
date: 2018-08-16
forum: General Help
---

### Post by sportscrazed2 on 2018-08-16
Long story short I ended up with a spare ssd the exact same make and model of current one running my os. Is it possible to setup automatic cloning of it so that in the event of a system failure i'm back up and running in 30 seconds or so?

---

### Post by TheFu on 2018-08-17
No, I don't think so.  Having the same UUID in the same physical machine at boot time will cause problems.  

But, there are other options, most will need a way to quiesce the file system for the backup/cloning to be successful. Backing up file systems that are currently being used is a roadmap for corrupt data.  It usually matters most for DB files which are active.

Using LVM and LVM-snapshots prior to making an image/backup is the general solution to this problem.  The real problem is the time it takes to copy all those bits.  If you don't use LVM-snapshots, then you must boot from alternate media to make the image. That can be a flash drive or external disk or 

You can connect the 2nd storage device as-needed, then use a low level clone method (dd, ddrescue, partimage, clonezilla, or fsarchiver) to get the bits from A to B. But at boot time, B cannot be connected or unexpected boot device will happen, at best.  Besides the fstab UUID issue, with a little scripting or manual intervention, you can clone, then fix the fstab as needed for the restore.

Or you can stop using UUIDs in the fstab. There are other methods, like paths which are just as uniquely addressable in the fstab.  Look in /dev/disk/by-path/ for the device names.   /dev/disk/by-path/pci-0000:00:1f.2-ata-1-part1 is an example.  The other fields of the fstab wouldn't change, just the 1st.

An alternative ... 
If you want a most efficient backup methods, a method that takes 1-3 minutes a day and no downtime.  Keep reading.

This breaks it down into LVM, LVM-snapshots, and rdiff-backup with LVM.
[https://category5.tv/shows/technology/episode/455/](https://category5.tv/shows/technology/episode/455/)
[https://category5.tv/shows/technology/episode/456/](https://category5.tv/shows/technology/episode/456/)
[https://category5.tv/shows/technology/episode/461/](https://category5.tv/shows/technology/episode/461/)
No magic. All commands are shown and explained.  The script for that show is similar to mine, but I add an --exclude-special-files option on all rdiff-backup stuff to avoid problems with ... er ... special files like fifos, pipes and devices. Backups really should be over a network and really should be "pulled", not "pushed" and not local to avoid malware problems.
Versioned backups are absolutely critical to any backup solution.  

If you have the rdiff-backup storage elsewhere (not on an ssd), then you can use rsync or rdiff-backup to pre-setup the SSD to work in an emergency. Just pull the old SSD and connect the replacement to the same, exact cable/slot, and all should be fine, assuming you modified the fstab to use paths instead of UUIDs.

---

### Post by Tadaen_Sylvermane on 2018-08-17
Not suggesting this is a backup but you can run the 2 ssds in raid 1. That will give you instant redundancy if a disk dies, no downtime. then just switch dead disk at your leisure. May need to reinstall for it though, not sure.

---


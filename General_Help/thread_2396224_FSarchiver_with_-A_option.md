---
title: "FSarchiver with -A option"
date: 2018-07-12
forum: General Help
---

### Post by rbmorse on 2018-07-12
I'm setting up a script that runs fsarchiver to "backup" the Linux partitions on my main workstation.  The target device is a separate, dedicated internal hard drive. All partitions involved except the EFI system partition are EXT4, no encryption or virtual filesystems in use. 

I know the -A option allows fsarchiver to operate on mounted partitions (live option). The man page doesn't specify, but does this mean that fsarchiver can be run "in background" while I'm using the machine for other tasks, or should it be in an otherwise quiescent state while fsarchiver is running?

I'm guessing the latter because afaIk Linux doesn't have a functional equivalent to VSS and in that case changing the content of the filesystem while fsarchiver was running could produce...interesting...results.  On the other hand, if it is possible to run fsarchiver in "background" it would be a simple matter to set up a cron job that would not require any user invertention. 

I'd appreciate it if someone who knows could share some knowledge.

---

### Post by TheFu on 2018-07-12
No.  This is a terrible idea.  

To use fsarchiver, if you expect to have uncorrupted backups, then you must boot from alternate media unless you are using LVM with snapshots or ZFS snapshots.  Any use of snapshots does require some storage be reserved to hold new data while the snapshot is frozen.  This can be tiny or it might be huge if you can't control all the processes on the system to prevent GB downloads during backup periods.

BTW, Linux has had LVM for decades. 

This is why choosing LVM during installation is something advanced users select.

So, you have a few choices, which is best depends on your specific setup.
* use LVM snapshots to freeze the file systems during backups; clearly LVM or ZFS must be pre-installed.
* Boot from a separate, minimal, OS that is always connected to the box and run fsarchiver against unmounted storage.
* Boot from separate, alternate media (flash, usb, whatever) and run fsarchiver against unmounted storage

Or you can use other backup methods that aren't imagers. There are lots of threads here outlining those.  Please stay away from tar.  Take a look at duplicity, duplicati, rdiff-backup, back-in-time, and a few other, similar tools.  Regardless of which you choose, if there are any DBMS systems running, you'll want to quiesce those (there are a few different ways) to prevent file corruption at restore time.

[https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots) - LVM Snapshot How-To
[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html) - Linux Documentation Project LVM-Snapshots

LVM2 has been very stable almost 2 decades, so don't worry too much about guides that seem old.

Linux expects admins to know how to avoid corrupt files.  If you don't take steps, then it isn't done.

---


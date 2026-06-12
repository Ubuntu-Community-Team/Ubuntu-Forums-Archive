---
title: "rsync across net hangs and reports problems with non-existent (temp?) files"
date: 2015-02-14
forum: General Help
---

### Post by elyse on 2015-02-14
Using 14.04 LTS. 
I'm trying to use rsync to back up to net-mounted shares. I am not sure whether the two problems I am seeing -- hangs and error messages -- are actually related.

I see similar problems with cifs mounts and nfs mounts.

The problems happen with or without compression. 

If --progress is not used the backup will progress for a while, then hang.

If --progress is used the backup will progress for a while, then hang with a file name showing, but no progress indicator. 

If I kill the rsync after it hangs, it spews out a bunch of messages like 
rsync: chown "/mnt/nebula/nfs/archive/home/dataraptors/vp/data-raptors.com/www/blog/tech/.waffles.comments.FMjV8O" failed: Operation not permitted (1)

Where /mnt/nebula/nfs is the destination mountpoint and neither the source nor destination directory contains a file named .waffles.comments.FMjV8O.
There is (now) a file waffles.comments in both the source and destination directories, but with different permissions. 
The destination directory also has permissions that look different from the source, and also end in an +.

(There may be similar messages put out in bunches early in the run before the hang.)

The cifs drive is a USB drive mounted on a router, the NFS drive is a WD MyCloud drive.

With the USB drive connected directly to the computer (type fuseblk) rsync does not generate the error messages and has progressed much farther without hanging.

Are there settings I can adjust for the CIFS and NFS mounts to avoid these problems?

---

### Post by SeijiSensei on 2015-02-14
Try using async as an NFS option, but be aware that you can lose data if the device is disconnected before a file is completely transferred.  Since you're backing up the NFS-mounted drive, that shouldn't be an issue.

---

### Post by elyse on 2015-02-14
Thank you. 

I will try that. It will be interesting to see if it helps.

I have found that rsync over ssh to the NAS server seems to work, so I have a way to do automatic backups, but I would still like to understand what is going on with the mounts.

---

### Post by nerdtron on 2015-02-14
You might also wanna try rsync with --partial option, which will keep partially transferred files. Helpful when transferring large files and interrupted in he middle.

---


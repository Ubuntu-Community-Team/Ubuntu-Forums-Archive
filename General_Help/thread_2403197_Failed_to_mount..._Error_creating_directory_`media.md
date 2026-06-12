---
title: "Failed to mount... Error creating directory `/media/eb': Permission denied."
date: 2018-10-08
forum: General Help
---

### Post by Razmear on 2018-10-08
[IMG]http://razmear.com/mounterror.png[/IMG]

This error occurs when trying to mount my USB stick, camera as mass storage, and my 2nd hard drive. 
Last night I installed NFS common and server so I could share filed between this PC and my MediaBox. 
The MediaBox is able to mount the share point from this machine, but not the other way around. However the bigger issue is I can not mount any device on my primary PC. 
It appears that Root has lost all permissions to /media. sudo mkdir results in Permission Denied. sudo mount -a exits silently with nothing mounted. Attempting to sudo chown root result in Operation Not Permitted. 
I've been searching for fixes for about 12 hours with no joy. 
fstab was edited last night when installing NFS, so I'm thinking that's part of the issue, but permissions look good. 
The system sees all my drives but gives the error above when mounting. (eb is my userid)
ls -al shows /media with 4096 not 0 as was another person's issue. 

At this point I don't even know what else to check. Any ideas would be appreciated.

---
Update. Just tried to insert a USB stick in my MediaBox and I'm getting the same error when trying to mount it. So it appears that installing NFS is definitely interfering with mounting other drives.

---

### Post by Razmear on 2018-10-08
Solved, sort of. 

Changed this line in fstab from: 
192.168.1.117:/srv/nfs  /media nfs  rsize=8192,wsize=8192,noexec,nosuid
To:
MediaBox:/srv/nfs  /media/test  nfs  rsize=8192,wsize=8192,noexec,nosuid
Rebooted and now I can mount my standard drives again. 
pretty sure it was bumping the mount point to /media/test that did the trick, but not 100% sure

Will now celebrate and then fix the MediaBox.

---


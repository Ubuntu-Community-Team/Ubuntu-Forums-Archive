---
title: "rsync failing with &quot;No space left on device (28) - which is wrong"
date: 2024-10-25
forum: General Help
---

### Post by Andrew_Benjamin on 2024-10-25
Hi all,

I have a 16TB Raid array which is ext3; I'm adding some drives and will need to convert to ext4.  The drive is mostly full with perhaps 60GB of free space.

I purchased a 20TB drive to serve as a temporary backup in case my expansion goes awry.

The 20 TB is on another machine on the same network and shared via Samba.  I mounted the Samba share on my 16TB array machine.

Using the command sudo rsync -av --inpace /media/RAID /mnt/20TBBackup the copying starts.

At random points the rsync will fail (it's nowhere near done/filling the new drive yet) and presents the message "rsync: write failed on /mnt20TBBackup/[the current at the time folder/file]: No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(393) [receiver=3.1.1]

When I restart rsync it picks up where it left off without complaint - until it fails again at some point down the road.  None of the files copied are large enough to  'fill' the 16TB drive while copying - the largest might be 5GB (?) so even if rsync is using the source drive as a temp drive, that shouldn't be the point of failure.

Could this be a bad disk?  A problem one of you geniuses will laughingly point out (I'll still happily say thank you) or something else?

Thanks.

Andrew

---

### Post by TheFu on 2024-10-26
Why would you mount using CIFS when you are using rsync?  I don't understand.  rsync easily transfers files over the network directly.

rsync -avz {source} {target}
where either the source or the target can be a remote system (not both).  The target looks like what you want to be remote above.  Also, sudo doesn't work with remote storage. The elevated privileges are dropped automatically and 'root' appears as 'nobody' unless you specifically setup remote root ssh access (which is usually a bad idea) Doesn't matter which network file sharing protocol is used.  CIFS is actually worse, since it is 1 userid, not all users on the system, unlike NFS.  But for this task, you should use rsync directly.

Also, learn the meaning of the trailing / in rsync commands. It is almost always best to use one.

So, 
```
sudo rsync -avz /media/RAID/ root@1.2.3.4:/path/to/20TBBackup/
```
Is probably the command you want, if the data files in  /media/RAID/ have different owners, groups, permissions, xattrs and ACLs.  Ensure that 
**sudo ssh root@1.2.3.4** works first.

The problem with failures is CIFS.  Don't use cifs.  Use rsync.

Whenever I install a new HDD, the first thing I do it run a SMART "long" test.  That can take over 24 hours to complete, depending on the HDD performance AND the interface used.

Just 1 more thing.  Putting storage that is mounted via fstab under /media is a bad idea for many reasons.

---

### Post by Andrew_Benjamin on 2024-10-27
sudo ssh root@... fails by not accepting the password (which works if I ssh into the machine directly).  Both machines are on the same network and I've tried  altering the machine starting the command (eg I've tried sudo ssh root@ from either machine to the other with the same failure).

So, like most things Linux, what am I failing to see here?

Andrew

---

### Post by TheFu on 2024-10-27
root is specifically prevented from using remote access in ubuntu.  This is one of those questions where it may be the best answer, but if you don't know how to allow it, perhaps you aren't ready for that level of security failure yet.

With CIFS, it is end-user-to-remote-storage so you will be losing many important aspects of files on Linux - the owner, group, permissions, xattrs, ACLs, and only keep the file contents.  Only you know if retaining just the file contents is sufficient or not.

Maybe if we step back completely and spell out in detail what the remote storage is, which OS it runs, how it can be controlled, and what the types of files to be copied there actually are, then we'll better be able to provide a solution?
For example, if the remote storage file system uses NTFS there are some issues.  IF the remote storage file system uses ext4, there are other considerations.

Yes, file systems and network protocols DO MATTER.

---

### Post by Andrew_Benjamin on 2024-10-27
I seem to have fixed my problem - thanks.  I'm copying away, so the suggestion worked (unless I time out).  But no need to reply unless I post back again (eg get the same out of space issue).

Thanks for the help.

Andrew

---


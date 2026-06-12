---
title: "Permissions to permit Plex to see directory on External Hard Drive"
date: 2015-01-27
forum: General Help
---

### Post by hophiphop on 2015-01-27
I am running Ubuntu 14.04 LTS
I have 2 external hard drives connected via USB.  Both were automatically mounted and were/are working fine. The 2 hard drives are known as 'External hard drive' and 'My Passport'.   I have a folder "Movies" on on one of them.

Yesterday I downloaded and installed Plex media server sucessfully.   When trying to configure Plex I can see both of the hard drives above but cannot browse directories on either.   I am able to browse the 'Linux 243gb' but I don't have capacity on this for my Movies directory.   My understanding is that Plex should be able to browse external hard disks without any problem or fancy footwork.

I assume the issue to be that the user "Plex" does not have permission to browse the directories in question.  I have tried unsuccessfully to amend the permissions of the directories.  I have tried changing directory ownership but whilst this does not fail neither does it work.

e.g.
craig@craig-Dimension-5100:/media/craig$ ls -l
total 20
drwx------  1 craig craig 12288 Jan 26 18:28 External hard drive
drwxrwxrwx 23 root  root   4096 Jul 30  2013 Linux 243gb
drwx------  1 craig craig  4096 Sep 23 15:30 My Passport
craig@craig-Dimension-5100:/media/craig$ sudo chown root:root /media/craig/'My Passport'
[sudo] password for craig: 
craig@craig-Dimension-5100:/media/craig$ ls -l
total 20
drwx------  1 craig craig 12288 Jan 26 18:28 External hard drive
drwxrwxrwx 23 root  root   4096 Jul 30  2013 Linux 243gb
drwx------  1 craig craig  4096 Sep 23 15:30 My Passport

**Can anyone explain how I should proceed to make these directories visible to Plex?**
 
craig@craig-Dimension-5100:/media/craig$ mount

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=craig)
/dev/sdh5 on /media/craig/Linux 243gb type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdh1 on /media/craig/External hard drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdf1 on /media/craig/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

craig@craig-Dimension-5100:/media/craig$ df

Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda5      237225664  90346348 135104492  41% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1017996         4   1017992   1% /dev
tmpfs             206268      1616    204652   1% /run
none                5120         0      5120   0% /run/lock
none             1031332       668   1030664   1% /run/shm
none              102400        68    102332   1% /run/user
/dev/sdh5      233398184 168380880  53138240  77% /media/craig/Linux 243gb
/dev/sdh1      737412288 593327208 144085080  81% /media/craig/External hard drive
/dev/sdf1      312537084 184195944 128341140  59% /media/craig/My Passport

---

### Post by hophiphop on 2015-01-27
Problem solved.  I found this piece [https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux) which I followed and sorted problem.  Drives are NTFS,

---

### Post by ajgreeny on 2015-01-27
I was really hopeful that you were going to solve one of my plex problems when I read the thread title, but unfortunately not.

I would like to do the same as you but with fat32 external flash drives which are sometimes brought round to our house with other peoples photos on.  I would love to be able to plug in the drive and show the photos on a smart TV client of my plexmediaserver but it's a no-go the same as your problem.  The plex folder browser can see any drive or folders on the external fat32 drives but it never sees any pictures in that folder or on the root of the drive.  I've searched the plex forums but it did not help.

Any thoughts?

---


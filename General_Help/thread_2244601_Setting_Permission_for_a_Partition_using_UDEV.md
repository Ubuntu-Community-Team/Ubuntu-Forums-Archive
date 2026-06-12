---
title: "Setting Permission for a Partition using UDEV"
date: 2014-09-17
forum: General Help
---

### Post by jeremy1701 on 2014-09-17
Hello,
I have my hard drive partitioned into two main drives; one that mounts as / and the other as /Data. I store all my music, documents, videos, etc on /Data. The /Data partition is automounted on login at /media/jeremy/Data. The / partition works as it should, however, /Data has some permission issues. Everything is mounted as 700, but I would like it to be mounted as 755. I cannot chmod permission on /Data at all. 

mount command gives the following
```

/dev/sda5 on /media/jeremy/Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

How can I create a UDEV rule that changes the permissions of /Data to 755 on automount?

---

### Post by oldfred on 2014-09-17
You show fuseblk, so is this NTFS or FAT32 formatted.
You cannot use chown or chmod on Windows formatted partitions.

What does ls -l show for your mount. Perhaps /media now is not as permissive?

But I have same default mount and open permissions on my NTFS (shared). And my data partition is ext3.

/dev/sdc2 on /mnt/shared type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

 fred@trusty-DT:/mnt/shared$ ls -l
total 3669
-rwxrwxrwx 1 fred root    8288 Nov 22  2009 calcAvetime.ods
-rwxrwxrwx 1 fred root   27384 Oct  9  2013 debug
drwxrwxrwx 1 fred root       0 Dec 28  2010 mozilla
drwxrwxrwx 1 fred root    8192 Oct  1  2012 OfficeFiles

   fred@trusty-DT:/mnt/shared$ cd /mnt/data
fred@trusty-DT:/mnt/data$ ls -l
total 128
drwxrwxr-x  3 fred fred  4096 May 29  2012 Calibre Library
drwxrwxr-x 20 fred fred 12288 Aug  3 14:45 Documents
drwxrwxr-x  9 fred fred 20480 Sep 11 23:55 Downloads

---

### Post by jeremy1701 on 2014-09-17
It is NTFS, but my permissions are locked down pretty tight. 

ls -la /media/

drwxr-xr-x+ 10 root root 4096 Sep 16 20:44 jeremy

ls -la /media/jeremy/

drwx------ 1 jeremy jeremy 12288 Jul 6 07:29 Data

Every folder in Data has the same permissions and owner.

---

### Post by oldfred on 2014-09-17
The only difference I can see is you are mounting in /media and I mount in /mnt.
Several versions ago they changed to include the user name in the default mount in /media. I assume that was so only the admin or booted user could then use temporary mounts in /media. 

I do prefer mounts to /mnt, but my main preference was that /mnt is not shown in Nautilus where /media is (was?) shown in Nautilus but would not work as already mounted. I already linked everything, so seeing it in Nautilus was not useful.

---

### Post by jeremy1701 on 2014-09-17
I was thinking a UDEV rule like 

ENV{ID_FS_TYPE}=="ntfs", ENV{mount_options}="$env{mount_options},gid=100,dmask=000,fmask=111,utf8"

might work, but it seems to have no effect on permissions.

---

### Post by oldfred on 2014-09-17
I do not know udev, but thought that was for auto mounts with Nautilus.

Your settings should be in fstab.

       Older systems with older version of NTFS-3g: 
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by jeremy1701 on 2014-09-18
Hello,
Thanks for your help. Setting the drive to mount using fstab and applying the appropriate umask worked.

---


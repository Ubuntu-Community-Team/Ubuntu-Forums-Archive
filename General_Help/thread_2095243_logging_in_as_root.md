---
title: "logging in as root"
date: 2012-12-16
forum: General Help
---

### Post by john vaughan on 2012-12-16
Hi, I am using Ubuntu 12.10 and am unable to back up to an external hard drive. Both Deja Vu and Back In Time tell me I dont have permission to write to the drive. I  didn't have this problem with 12.04. Any help would be appreciated.

---

### Post by john vaughan on 2012-12-16
Hi, I think I need to log in as root in Ubuntu 12.10 to back up my files as the backup software ( Deja Vu and Back In Time ) tells me I don't have permission to write to the external hard drive I am using. I checked the proerties of the external drive and it said it belonged to root. How can I log in as root. I was using Xubuntu 12.04 before and it gave me the opyion of logging in as root. I also had no problems using Back In Time with the same external hard drive. Thanks for any help.

---

### Post by The Cog on 2012-12-16
You don't need to log in as root, it is something that is to be discouraged because you shouldn't be working as root any more than really necessary.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can raise an existing command prompt to root by entering the command
```
sudo -i
```
Or launch a graphical application (such as nautilus file manager) with the command
```
gksu nautilus
```
Be extra careful when operating as root - you have the ability to trash the entire system.

---

### Post by coffeecat on 2012-12-16
Threads merged - same issue.

@john vaughan, I think you're going about this the wrong way. If you invoke root privileges to backup your files to your external drive, then any backed up files will be owned by root which will cause inconvenience in the long term. It would be better to look at the ownership of your external drive. I suspect it is formatted ext3/4 and automounted from the file manager. It is very easy to change its ownership and permissions so that you do not have this problem.

Mount the external drive and post the output of these commands:

```
mount
sudo fdisk -lu
sudo blkid
```

---

### Post by john vaughan on 2012-12-16
Thanks Cog. I don't really want to log in as root but can't seem to back up to the external hard drive and it tells me it "belongs" to root.

---

### Post by john vaughan on 2012-12-16
Hi Coffeecat, results are as follows,
 mount
/dev/sda1 john@john:~$ sudo blkid
/dev/sda1: UUID="4cf9380d-8bf7-47db-99df-215a7b1993d8" TYPE="ext4" 
/dev/sda5: UUID="33d81917-cb2c-4452-86d8-8d3e5aabd71c" TYPE="swap" 
/dev/sdb1: UUID="43423f4c-6316-410a-8733-72969f3d1137" TYPE="ext4" 
john@john:~$ 
ton / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /tmp/guest-h5aWJD type tmpfs (rw,mode=700)
gvfsd-fuse on /run/user/john/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=john)
/dev/sdb1 on /media/john/43423f4c-6316-410a-8733-72969f3d1137 type ext4 (rw,nosuid,nodev,uhelper=udisks2)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b86bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1941538815   970768384   83  Linux
/dev/sda2      1941540862  1953523711     5991425    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1941540864  1953523711     5991424   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773119   488385536   83  Linux
john@john:~$ 

john@john:~$ sudo blkid
/dev/sda1: UUID="4cf9380d-8bf7-47db-99df-215a7b1993d8" TYPE="ext4" 
/dev/sda5: UUID="33d81917-cb2c-4452-86d8-8d3e5aabd71c" TYPE="swap" 
/dev/sdb1: UUID="43423f4c-6316-410a-8733-72969f3d1137" TYPE="ext4" 
john@john:~$ 
 This means nothing to me but I hope you can help.
Thanks again.

---

### Post by coffeecat on 2012-12-16
Your external drive is formatted ext4. At the moment it is owned by root but you can change the ownership by chowning the mountpoint while it is mounted. The mountpoint does not get chowned, but the filesystem itself does.

I'll assume that your external drive is still mounted on  /media/john/43423f4c-6316-410a-8733-72969f3d1137, but check this by running the mount command first. Simply run these two terminal commands:

```
sudo chown john: /media/john/43423f4c-6316-410a-8733-72969f3d1137
sudo chmod 777  /media/john/43423f4c-6316-410a-8733-72969f3d1137
```

Don't forget the trailing colon in "john:" in the first command; this ensures that the filesystem is owned by your default group. Also - if you are going to be the only user of this drive then the second chmod command is not necessary. The chmod command will allow anyone to read-write to the drive.

---

### Post by ajgreeny on 2012-12-16
This is just a very minor point, but I find it much easier to label my external ext3 partition (using either gparted or tune2fs) to something descriptive and therefore much easier to use than the UUID shown above.  The disk/partition will then always be mounted at **/media/*user/label*** in 12.10, or simply **/media/*label*** in earlier versions of Ubuntu.

If you're happy with the UUID, no problem; it will still work in exactly the same way.

---

### Post by john vaughan on 2012-12-16
Hi again Coffeecat. I carried out your instructions and they worked like a dream so thankyou very much for your time. Just as an aside, where can I learn about this sort of stuff?
Also thanks to everyone else for their suggestions.

---

### Post by JKyleOKC on 2012-12-16
> **john vaughan said:**
> Hi again Coffeecat. I carried out your instructions and they worked like a dream so thankyou very much for your time. Just as an aside, where can I learn about this sort of stuff?
Also thanks to everyone else for their suggestions.Right here is one of the best ways I know to learn such stuff. I habitually click the "New Posts" button near the top of the page each time I log into the forums, and that's several times a day -- whenever I run out of things that need immediate attention.

Keep in mind that it's a support area, so most of the new messages are from people with problems. However you'll quickly come to recognize the people who respond with good solutions for them, and you'll also get a good feel for the most common causes of the problems themselves.

You can also find all kinds of good information in the wiki that I reference in my sig below; it's not just about marking a thread as solved.

---


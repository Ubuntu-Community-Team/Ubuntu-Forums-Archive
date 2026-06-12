---
title: "Quota Configuration - NAS RAID"
date: 2022-02-04
forum: General Help
---

### Post by penguinpages2 on 2022-02-04
Ubuntu: buster
Hardware: NAS Appliance GNUBee 
CPU: 2core MIPS 1004Kc V2.15

Issue:  I have cameras streaming to ftp server which keep using too much space. I use to have dedicated disk volume for them but that old system is dead.. The new one I have to lean into quotas to limit their space use and force FIFO


# Enable quotas on user "camera" and so file capacity on NAS consumed
apt install  quota quotatool -y
vi /etc/fstab  # [How To Set Filesystem Quotas on Ubuntu 18.04 | DigitalOcean ]("https://www.digitalocean.com/community/tutorials/how-to-set-filesystem-quotas-on-ubuntu-18-04")
[TABLE]
[TR]
[TD]# UNCONFIGURED FSTAB FOR BASE SYSTEM
LABEL=GNUBEE-ROOT /  ext4  noatime,errors=remount-ro 0  1
/dev/mmcblk0p1  none    swap    sw      0 0
[COLOR=#ff0000]LABEL=md0       /media/md0  ext4 defaults,quota,usrquota,grpquota 0 0[/COLOR][/TD]
[/TR]
[/TABLE]

touch /media/md0/aquota.group
chmod 660  /media/md0/aquota.group
mount -o remount /media/md0
quotaon -av
edquota -g camera
setquota -u camera 100G 120G 0 0 /media/md0/
setquota -g camera 100G 120G 0 0 /media/md0/
quota -vs camera
repquota -a
 
tail -f /var/log/syslog
Feb  4 13:21:31 pandora kernel: [256770.589642] EXT4-fs (md0p1): quota option not supported
Feb  4 13:21:31 pandora kernel: [256770.600276] EXT4-fs (md0p1):[COLOR=#ff0000] usrquota option not supported[/COLOR]
Feb  4 13:21:31 pandora kernel: [256770.611430] EXT4-fs (md0p1): [COLOR=#ff0000]grpquota option not supported[/COLOR]
Feb  4 13:21:32 pandora kernel: [256770.634324] EXT4-fs (md0p1): re-mounted. Opts: quota,usrquota,grpquota




I also tried 
LABEL=md0       /media/md0  ext4 defaults,usrjquota=quota.user,grpjquota=quota.group  0 0

Feb  4 13:10:32 pandora kernel: [256111.563966] EXT4-fs (md0p1): [COLOR=#ff0000]usrjquota=quota.user option not supported[/COLOR]
Feb  4 13:10:32 pandora kernel: [256111.577229] EXT4-fs (md0p1): [COLOR=#ff0000]grpjquota=quota.group option not supported[/COLOR]
Feb  4 13:10:33 pandora kernel: [256111.603035] EXT4-fs (md0p1): re-mounted. Opts: usrjquota=quota.user,grpjquota=quota.group
Feb  4 13:17:01 pandora CRON[25654]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


root@pandora:/media/md0/camera# quota --version^C
root@pandora:/media/md0/camera# find /lib/modules/`uname -r` -type f -name '*quota_v*.ko*'
root@pandora:/media/md0/camera#




Not sure if this is a function of the kernel and modules I have on this system, or that the documentation is just not clear.

---

### Post by TheFu on 2022-02-05
There is no "buster" version of Ubuntu.

Don't quotas have to be enforced on the DAS side, not over network connections?  Perhaps the client or the server are too old?
[https://stackoverflow.com/questions/29362617/how-to-set-quota-or-limits-on-nfs-share-on-the-client](https://stackoverflow.com/questions/29362617/how-to-set-quota-or-limits-on-nfs-share-on-the-client)  Some NAS appliances are known not to support the full set of expected commands.

As a workaround, I'd use a **find /restrictive/path -mtime {hours} -delete** method to remove files over a specific age from specific areas of the system on a daily basis.  If you have less than 2 weeks of storage, perhaps 2x a day or 4x a day running a cleanup would work?

This is a very common model. I use it on nearly all my systems, daily.

If the filenames are all the same, I'd look into a rotation script. That's basically, 
```
mv file-9 file-10
mv file-8 file-9 
mv file-7 file-8 
mv file-6 file-7 
mv file-5 file-6 
mv file-4 file-5 
mv file-3 file-4 
mv file-2 file-3 
mv file-1 file-2
```
You could use a loop instead or just point **logrotate** at the files. Of course, the number of files retained can be any number, but you really want to prevent any directory from having more than about 500 files inside it. There is an added risk of directory corruption, then all files could be lost/misplaced. Logrotate has a rotation capability built in. It can also compress files after the first 1 or 2, but for pre-compressed files (images/media), that is a wasted effort.

Quotas are more about limiting 20+ userids to a limited amount of storage used fairly. When a userid's quota is full, it cannot write any more. It isn't a FIFO.

---

### Post by penguinpages2 on 2022-02-07
I was trying to enforce quotas on NAS / disk side.  But adding option to disk did not work.  It implies the kernel module is not compiled.

Hoping that I missed something.   Or that maybe others have notes on how to compile the module for disk quota.

---


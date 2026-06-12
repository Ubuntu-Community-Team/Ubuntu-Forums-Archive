---
title: "Cannot mount external hdd, no privileges"
date: 2013-12-17
forum: General Help
---

### Post by yoramdavid on 2013-12-17
Hello all.

After spending all afternoon reading threads about this and not finding a solution that worked for me, I decided to post a threat on this again:

I have an external hdd formatted as NTFS that I want to mount at a fixed mount point named "A-Data" in /media.
So I created a mount point for it and added an entry in fstab as follows:

```
UUID=3C607E73607E342C   /media/A-Data 		ntfs  	defaults,noauto,nls=utf8,umask=0222,user,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
```

However, I cannot mount it.

I get this error message:

```
An error occurred while accessing 'Yoram-A-Data', the system responded: A operação pedida foi mal-sucedida.: Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged
```

Any help would be appreciated.

The whole fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb5 :
UUID=f5c2fda7-0eeb-4890-bd17-e8f59cc7602b	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=71135240-e9ac-4277-bccc-da52109b9943	/boot	ext4	defaults	0	2
#Entry for /dev/sdb6 :
UUID=22d2b552-cfc9-4e41-b6de-172b694ace2c	/home	ext4	defaults	0	2
#Entry for /dev/sda5 :
UUID=79728FFDFDD66EC6	/media/ARQUIVOS	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdd5 :
UUID=11FC2C34D54F2529	/media/JOGOS	ntfs	defaults,noauto,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
UUID=61A60666D74790D6	/media/MULTIMEDIA	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdd1 :
UUID=120B4E126D0CC231	/media/PROGRAMAS	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdb7 :
UUID=CA1480BC1480AD4F	/media/TRABALHANDO	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdb2 :
UUID=D208D12E08D11279	/media/WINDOWS_XP	ntfs	defaults,noauto,nls=utf8,umask=0222	0	0
#Entry for /dev/sdd1:
UUID=3C607E73607E342C   /media/A-Data 		ntfs  	defaults,noauto,nls=utf8,umask=0222,user,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdd6 :
UUID=f06adac3-0f96-4d5f-b58b-ad74625d29f9	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
```

The other partitions are mounted just fine.

Thank you

---

### Post by oldfred on 2013-12-17
I do not think you can have both umask and fmask & dmask as the umask will conflict with the other two.
 fmask and dmask Like umask but defining file and directory respectively individually. 



 From user Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

---

### Post by yoramdavid on 2013-12-18
> **oldfred said:**
> I do not think you can have both umask and fmask & dmask as the umask will conflict with the other two.
 fmask and dmask Like umask but defining file and directory respectively individually. 



 From user Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

Thanks oldfred,

I have removed the umask option, but nothing has changed.

---

### Post by oldfred on 2013-12-18
I do not know details of mount commands well enough, but do not see anything else.
Does that NTFS partition need chkdsk?

---

### Post by yoramdavid on 2013-12-18
> **oldfred said:**
> I do not know details of mount commands well enough, but do not see anything else.
Does that NTFS partition need chkdsk?

Not sure what you mean with that, but I know the disk is fine as if I comment the line concerning that hdd, it mounts fine.
But I want it to have a fixed mount point.

---

### Post by oldfred on 2013-12-18
Better info here on settings:
 From user Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

---

### Post by yoramdavid on 2013-12-20
> **oldfred said:**
> Better info here on settings:
 From user Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

I changed the dmask and fmask to those values (dmask=775,fmask=664 and dmask=002,fmask=113) as I was confused about which I was supposed to enter, no luck.
I have that problem only with drives I do not automount at startup.
All other mount fine.

I now get this error: 
```
An error occurred while accessing 'Pasta Pessoal', the system responded: A operação pedida foi mal-sucedida.: Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdh1 on /media/A-Data
```

The line looks like this:
```
UUID=3C607E73607E342C   /media/A-Data 		ntfs  	noauto,defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0

```

---

### Post by oldfred on 2013-12-20
I do not know options well. But does not noauto mean you have to manually mount it as root?
Would be easier than just to have a script with the mount and run the script if you do not want it mounted when booting, but then do want it later.

---

### Post by yoramdavid on 2013-12-21
> **oldfred said:**
> I do not know options well. But does not noauto mean you have to manually mount it as root?
Would be easier than just to have a script with the mount and run the script if you do not want it mounted when booting, but then do want it later.

I do not much about it either. I know noauto does not mount it automatically. The drive is external and not plugged all the time, the other drives I do not want them to be mounted unless I really need them.
There must be a way to do this, to give the user permission to mount it.
I have read on other threads, that if you add the "user" or "users" option, it gives permission to the current user or all users respectively, but it does not work.

Thanks for your help.

---

### Post by yoramdavid on 2013-12-29
I configured the NTFS utility and checked the boxes for internal hdd support as well as external hdd support, rebooted and there were errors mounting the internal hdd set to automount, during the boot time. I had to press S to skip mounting.
I disabled the support and had to change the fstab to its original values or nothing would mount.

So, my problem persists. I have read many threats on this on the net, so this seems to be a common problem. I have a few several "solutions" but none worked for me.
I followed this thread: [http://ubuntuforums.org/showthread.php?t=1661757](http://ubuntuforums.org/showthread.php?t=1661757), nothing.

Any help would be appreciated.

---

### Post by oldfred on 2013-12-29
Repost entire fstab and UUIDs. Since longer use code tags.

       sudo blkid -c /dev/null -o list

---

### Post by yoramdavid on 2013-12-30
Thanks, oldfred

My fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb5 :
UUID=f5c2fda7-0eeb-4890-bd17-e8f59cc7602b	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=71135240-e9ac-4277-bccc-da52109b9943	/boot	ext4	defaults	0	2
#Entry for /dev/sdb6 :
UUID=22d2b552-cfc9-4e41-b6de-172b694ace2c	/home	ext4	defaults	0	2
#Entry for /dev/sdd1 :
#UUID=3C607E73607E342C	/media/A-Data		ntfs	noauto,defaults,nosuid,nodev,nls=utf8,umask=0222,user,rw,exec,windows_names,hide_hid_files	0	0
#Entry for /dev/sda5 :
UUID=79728FFDFDD66EC6	/media/ARQUIVOS		ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdc5 :
UUID=11FC2C34D54F2529	/media/JOGOS		ntfs	noauto,defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sda1 :
UUID=61A60666D74790D6	/media/MULTIMEDIA	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdc1 :
UUID=120B4E126D0CC231	/media/PROGRAMAS	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdb7 :
UUID=CA1480BC1480AD4F	/media/TRABALHANDO	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdb2 :
UUID=D208D12E08D11279	/media/WINDOWS_XP	ntfs	noauto,defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,windows_names,hide_hid_files	0	0
#Entry for /dev/sdc6 :
UUID=f06adac3-0f96-4d5f-b58b-ad74625d29f9	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0

```
There is an empty line at the end.


```
$ sudo blkid -c /dev/null -o list
device                                               fs_type         label            mount point                                              UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                              ext4                             /boot                                                      71135240-e9ac-4277-bccc-da52109b9943                                                                                                                                                                                 
/dev/sda2                                              ntfs            WINDOWS XP       (not mounted)                                              D208D12E08D11279                 
/dev/sda5                                              ext4                             /                                                          f5c2fda7-0eeb-4890-bd17-e8f59cc7602b                                                                                                                                                                                 
/dev/sda6                                              ext4                             /home                                                      22d2b552-cfc9-4e41-b6de-172b694ace2c                                                                                                                                                                                 
/dev/sda7                                              ntfs            TRABALHANDO      /media/TRABALHANDO                                         CA1480BC1480AD4F                 
/dev/sdb1                                              ntfs            PROGRAMAS        /media/PROGRAMAS                                           120B4E126D0CC231                 
/dev/sdb5                                              ntfs            JOGOS            (not mounted)                                              11FC2C34D54F2529                 
/dev/sdb6                                              swap                             <swap>                                                     f06adac3-0f96-4d5f-b58b-ad74625d29f9                                                                                                                                                                                 
/dev/sdc1                                              ntfs            MULTIMEDIA       /media/MULTIMEDIA                                          61A60666D74790D6                 
/dev/sdc5                                              ntfs            ARQUIVOS         /media/ARQUIVOS                                            79728FFDFDD66EC6                 
/dev/sdh1                                              ntfs            Yoram-A-Data     (not mounted)                                              3C607E73607E342C 

```

I cannot mount any of the drives that are not mounted automatically during boot time.
Yoram-A-Data is an external hdd.

---

### Post by oldfred on 2013-12-30
I do not see anything.
So all the internal drives mount correctly and only the external has issues.
Some have issues mounting externals in fstab as they have sped up boot process but external drives do not always come up to speed fast enough.

You still show a umask for NTFS, but not sure if that is the issue.

 From user Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)
At the moment of birth every file has permissions of 666 and every directory has permissions of 777. A system wide umask is created to modify these permissions immediately after birth and it's currently set at 002. So when you create a new file it's permissions are:
File: 666 - 002 = 664
Folder: 777 - 002 = 775

   At the moment of birth NTFS files and folders start out with exactly the same permissions: 777. 
So if you set up fstab this way for an NTFS partition: dmask=002,fmask=113
File: 777 - 113 = 664
Folder: 777 - 002 = 775

   If you used a umask of 002 on NTFS then 777 - 002 makes every file excuteable which you do not want.

---

### Post by Habitual on 2013-12-30
I use 
```
rw,uid=1000,gid=100,dmask=022,fmask=133 0 0
``` with the ntfs-3g driver (Not an ubuntu system) and I get 
good perms and ownership.

Files = 644
and
Directories come out 755.

Good luck.

---

### Post by yoramdavid on 2013-12-31
> **oldfred said:**
> I do not see anything.
So all the internal drives mount correctly and only the external has issues.
Some have issues mounting externals in fstab as they have sped up boot process but external drives do not always come up to speed fast enough.

You still show a umask for NTFS, but not sure if that is the issue.

 From user Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)
At the moment of birth every file has permissions of 666 and every directory has permissions of 777. A system wide umask is created to modify these permissions immediately after birth and it's currently set at 002. So when you create a new file it's permissions are:
File: 666 - 002 = 664
Folder: 777 - 002 = 775

   At the moment of birth NTFS files and folders start out with exactly the same permissions: 777. 
So if you set up fstab this way for an NTFS partition: dmask=002,fmask=113
File: 777 - 113 = 664
Folder: 777 - 002 = 775

   If you used a umask of 002 on NTFS then 777 - 002 makes every file excuteable which you do not want.

All internal drives that are set to mount at boot, ie do not have the option "noauto" mount correctly.
The two internal drives that have the "noauto" option, do not mount at boot time and do not mount manually either unless with root permission
The same goes with the external drive.

I have then tried what you suggested: dmask=664 and fmask=775 with no luck.
I do not see any umask on my fstab, not sure what you are talking about.

Thanks.
_David

---

### Post by yoramdavid on 2013-12-31
> **Habitual said:**
> I use 
```
rw,uid=1000,gid=100,dmask=022,fmask=133 0 0
``` with the ntfs-3g driver (Not an ubuntu system) and I get 
good perms and ownership.

Files = 644
and
Directories come out 755.

Good luck.

Hi Habitual,
I tried this as well, but you have not the "noauto" option which makes all the difference I think, your drives are being mounted at startup, mines (those I want to only mount manually) are not.
I have perms and ownership as well on mines which mount at startup.

Thanks.

---


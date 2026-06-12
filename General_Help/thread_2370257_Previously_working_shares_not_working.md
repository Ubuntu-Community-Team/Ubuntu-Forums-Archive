---
title: "Previously working shares not working"
date: 2017-09-01
forum: General Help
---

### Post by Jeffrey_Becker on 2017-09-01
I have several USB connected drives that are used in my various server applications. I have windows shares configured and permissions for all users set in Windows.
It's a static IP and I verified it has not changed. The drives are available on the Windows 10 host and the Linux guest (hyper-v) can ping the IP.
mount -a gives an error about a missing library, namely UTF8, which is defined in the fstab.
I've tried removing the definition. I upgraded all packages that were not upgraded. I removed packages that were set to auto remove. I've tries various charsets and tried removing sec=ntlm
**I read in another thread that windows may require a version number be defined but I wouldn't know which version to test.**
-----
EDIT
The bold text above was the answer. In fstab I define cifs but now if the remote connection is windows you have to define the version. It is supposed to default to ver3 but it didn't anymore on my system
-----
Here are my various outputs.

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
#UUID=eb7e62cf-b386-4cef-8a18-57a52b191d1f /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
#UUID=351E-2AF5  /boot/efi       vfat    defaults        0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#UUID=eb7e62cf-b386-4cef-8a18-57a52b191d1f    /boot    ext2    defaults    0    2
UUID=351E-2AF5    /boot/efi    vfat    defaults    0    1
##Mounted Windows shares
//192.168.0.14/DataDisk /mnt/jnjincaData cifs credentials=/.windowscredentials,gid=jnjinca,iocharset=utf8,sec=ntlm 0 0
//192.168.0.14/owncloudDrive /mnt/owncloudData cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=33,gid=33,file_mode=0770,dir_mode=0770,iocharset=utf8,sec=ntlm 0 0
//192.168.0.14/emby /mnt/emby cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=120,gid=129,file_mode=0770,dir_mode=0770,iocharset=utf8,sec=ntlm 0 0
//192.168.0.14/emby /mnt/owncloud-emby cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=33,gid=33,file_mode=0770,dir_mode=0770,iocharset=utf8,sec=ntlm 0 0
```

```
root@ubuntu:/home/jnjinca# mount -a
mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

```

root@ubuntu:/home/jnjinca# dmesg
[ 1670.189715] CIFS VFS: CIFS mount error: iocharset utf8 not found
[ 1670.192049] CIFS VFS: CIFS mount error: iocharset utf8 not found
[ 1670.194398] CIFS VFS: CIFS mount error: iocharset utf8 not found
[ 1670.197554] CIFS VFS: CIFS mount error: iocharset utf8 not found

```

```
root@ubuntu:/home/jnjinca# locale
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

```

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/lib/modules/"
``` 
I added /lib/modules to try and get it to locate my UTF files since nls_utf8.ko is located in /lib/modules/4.4.0-93-generic/kernel/fs/nls

---

### Post by Jeffrey_Becker on 2017-09-02
Well I haven't gotten a response here yet but I think I'll look into steps here [https://lists.samba.org/archive/samba/2015-March/190157.html](https://lists.samba.org/archive/samba/2015-March/190157.html)
Or I'll just set up resource sharing between the host and guest and mount through USB or eSATA directly instead.

I did find that my workgroup name was not defined correctly but it didn't resolve the issue.

another edit. 
This is currently my /etc/fstab file, the first share now mounts correctly. the others give input/output errors. I'm thinking it's a permissions thing but I removed all the perms and uid,gid info and got the same thing.
I just verified my uid and gid haven't changed for the other 3 shares.
```

//192.168.0.14/DataDisk /mnt/jnjincaData cifs credentials=/.windowscredentials,gid=jnjinca,sec=ntlm 0 0
//192.168.0.14/owncloudDrive /mnt/owncloudData cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=33,gid=33,file_mode=0770,dir_mode=0770,sec=ntlm 0 0
//192.168.0.14/emby /mnt/emby cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=120,gid=129,file_mode=0770,dir_mode=0770,sec=ntlm 0 0
//192.168.0.14/emby /mnt/owncloud-emby cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=33,gid=33,file_mode=0770,dir_mode=0770,sec=ntlm 0 0
```

I'm on day 3 of this, getting a little flustered. :(

---

### Post by Jeffrey_Becker on 2017-09-02
```
jnjinca@ubuntu:~$ echo $LANG
en_US.UTF-8
jnjinca@ubuntu:~$ !echo $NLS_LANG
echo $LANG $NLS_LANG
en_US.UTF-8

```

---

### Post by Jeffrey_Becker on 2017-09-02
at this point i'm thinking this is a kernel bug. I'm trying to load a different charset and getting charset not found. I've tried manually enabling the utf8 module. If that doesn't work I'll try rolling back to the old kernel.

Well if it's a kernel error it's happening in a few different kernel versions.

---

### Post by Jeffrey_Becker on 2017-09-02
```
[  767.304184] CIFS VFS: cifs_mount failed w/return code = -5
```
I'm still getting the same error on three different kernel versions. I don't know what to do next

I completely removed, purged, reinstalled cifs-utils, samba.. I even created a new share

The craziest thing is that this share works with the exact same setup.
//192.168.0.14/DataDisk /mnt/jnjincaData cifs credentials=/.windowscredentials,gid=jnjinca,iocharset=utf8,sec=ntlm 0 0

I just copied all the windows ownership and permissions from the drive that works and no luck.

---

### Post by Jeffrey_Becker on 2017-09-03
Well it would appear I had to tell my system what version of samba to use and define vers=3.0 at the end of each of my fstab entries.
Here's an example entry
```
//192.168.0.14/owncloudDrive /mnt/owncloudData cifs nosuid,nodev,noexec,credentials=/.windowscredentials,uid=33,gid=33,file_mode=0770,dir_mode=0770,iocharset=utf8,sec=ntlm,vers=3.0 0 0
```

Moving 516GB of shows and movies back.. My backup plan was to format the drive as ext4 and make it offline in windows so my guest linux could see it.

---


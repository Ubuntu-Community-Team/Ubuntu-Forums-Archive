---
title: "Cannot change the permissions of files on internal hdd ntfs partition"
date: 2013-02-02
forum: General Help
---

### Post by drunkenbrawler on 2013-02-02
Hi,

I have ubuntu 12.04 installed on my Dell-XPS-15z. The problem I am facing is, I am not able to modify file permissions on the mounted partitions, but I can do that in my home directory.  The partition I am using is ntfs.

I have used previous versions of ubuntu and I have not faced this problem before. I have ntfs-3g and ntfs-config installed. I have tried setting different things in fstab like fmask etc, but again, it sets the permissions and wont let me change anything.

Following is the output copied from my terminal.

Home directory
```

[aniket @ aniket-XPS-15z : ~]$ ls -l a.out 
-rw-rw---- 1 aniket aniket 8377 Jan 22 14:57 a.out
[aniket @ aniket-XPS-15z : ~]$ chmod 755 a.out 
[aniket @ aniket-XPS-15z : ~]$ ls -l a.out 
-rwxr-xr-x 1 aniket aniket 8377 Jan 22 14:57 a.out
[aniket @ aniket-XPS-15z : ~]$

```

mounted partition

```

[aniket @ aniket-XPS-15z : Aniket's_]$ touch foo
[aniket @ aniket-XPS-15z : Aniket's_]$ ls -l foo
-rw------- 1 aniket aniket 0 Feb  2 11:54 foo
[aniket @ aniket-XPS-15z : Aniket's_]$ chmod 777 foo 
[aniket @ aniket-XPS-15z : Aniket's_]$ ls -l foo
-rw------- 1 aniket aniket 0 Feb  2 11:54 foo
[aniket @ aniket-XPS-15z : Aniket's_]$ 

```

output of df -T and ubuntu release

```

[aniket @ aniket-XPS-15z : Aniket's_]$ df -T
Filesystem     Type     1K-blocks      Used Available Use% Mounted on
/dev/sda6      ext4      36289240   9712516  24733320  29% /
udev           devtmpfs   2990768         4   2990764   1% /dev
tmpfs          tmpfs      1201132       884   1200248   1% /run
none           tmpfs         5120         0      5120   0% /run/lock
none           tmpfs      3002824       228   3002596   1% /run/shm
/dev/sda5      fuseblk  354506320 195613584 158892736  56% /media/Aniket's_

```
```

[aniket @ aniket-XPS-15z : Aniket's_]$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
[aniket @ aniket-XPS-15z : Aniket's_]$

```

The partition was mounted when I navigated the partition using nautilus.
Any help will be much appreciated.

Thanks.

---

### Post by oldfred on 2013-02-02
NTFS being a Windows file system does not have Linux file ownership & permissions. You set a default with the mount in fstab?

       [https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Example
       from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
For ntfs UUID shown is example only see below:
```
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

            sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
       
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

     Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by drunkenbrawler on 2013-02-02
Thanks a lot for reply.

I can mount partitions but was confused as I was not able to modify permissions in usual way.
Just to re-iterate what I got to know -
> 
NTFS permissions are set at the time of mount and can not be changed in usual way after the mount. If you want to change the permissions, you have to re-mount with different mask (which will set the same permission for all the files).

Is that correct?

Thanks.

---

### Post by oldfred on 2013-02-02
Generally the NTFS does not have permissions and is being shared with Windows and is just data. So permissive permissions are usually ok, just to make it easy to use.

Again I refer to Morbuis1 as he understands this.

       From Morbuis1
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)
At the moment of birth every file has permissions of 666 and every directory has permissions of 777. A system wide umask is created to modify these permissions immediately after birth and it's currently set at 002. So when you create a new file it's permissions are:
File: 666 - 002 = 664
Folder: 777 - 002 = 775


       
 If you used a umask of 002 on NTFS then 777 - 002 makes every file excuteable which you do not want.

---

### Post by drunkenbrawler on 2013-02-06
Thanks a lot. That helps.

---


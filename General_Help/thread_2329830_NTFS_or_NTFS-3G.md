---
title: "NTFS or NTFS-3G"
date: 2016-07-05
forum: General Help
---

### Post by hornetster on 2016-07-05
Wondering when mounting the NTFS fiilesystem for read/write (general use), should I be using "ntfs" or "ntfs-3g" in fstab, and what options should be used when mounting on boot?
Thanks.

---

### Post by oldfred on 2016-07-05
I believe either works.

I still use Morbius' template to paste into my fstab with my UUID. I prefer to use /mnt/shared. And set Windows system partition as read only or hidden. Only share a NTFS data partition. And if newer Windows you must have fast start up or always on hibernation off.

       [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 

      
 # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

---

### Post by Morbius1 on 2016-07-05
Just ran this in Ubuntu 16.04 in case something changed:
> tester@vub1604:~$ ls -l /sbin/mount.ntfs
lrwxrwxrwx 1 root root 13 Apr 23 18:14 /sbin/mount.ntfs -> mount.ntfs-3g
It would appear that "ntfs" is still a symbolic link to "ntfs-3g".

---

### Post by hornetster on 2016-07-06
Thanks for the replies.
Can assume they are the 'same', then....
Thanks.

---


---
title: "Files auto-mounts ntfs partition. Is it ok for me to add that to fstab?"
date: 2018-01-29
forum: General Help
---

### Post by bvz on 2018-01-29
Hi,

I've tried to search around the web for an answer to this question before posting here.  Unfortunately I have not been able to figure it out. I am running 17.10

I have a machine with several ntfs partitions as well as several ext4 partitions. One ntfs partition has a label of "Data". The other has a label of "OS".

What I would like to do is permanently mount the "Data" ntfs partitions as:

/data


If I open this location (/dev/nvme0n1p4) in Files, it will be mounted in:

/media/<user>/Data

My question is: If I permanently mount the "Data" ntfs partition as "/data" using fstab, will that get confused with Files?  I.e. will Files try to mount it a separate time under the above path if I click on it? Or will Files recognize that this partition is already mounted and not try to re-mount it in its preferred location?

I am afraid to just try it for fear of borking my system.

Thanks!

---

### Post by Impavidus on 2018-01-29
If you use fstab to mount the partition somewhere, Files (aka Nautilus or the file manager) won't show it as a separate partition. You can safely add your data partition to fstab.

---

### Post by oldfred on 2018-01-29
If your mount is in /home or in /media then it will be directly shown in Naulitus.
If mounted in other places, it will not be directly shown and you have to go to Computer and drill down to location. 
But you can link folders from any mount into /home if desired (what I do).

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 

Always run this before rebooting after editing fstab. It remounts using new fstab, and if no errors you are ok. Otherwise you must fix errors before rebooting.
sudo mount -a

      
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by sisco311 on 2018-01-29
> **oldfred said:**
> If your mount is in /home or in /media then it will be directly shown in Naulitus.
If mounted in other places, it will not be directly shown and you have to go to Computer and drill down to location. 


You can also use the x-gvfs-hide and x-gvfs-show mount options explicitly to override this policy: [https://github.com/GNOME/gvfs/blob/master/monitor/udisks2/what-is-shown.txt](https://github.com/GNOME/gvfs/blob/master/monitor/udisks2/what-is-shown.txt)

---

### Post by bvz on 2018-01-29
Wow, thanks for all the fantastic help! I'll make the changes tonight!

---


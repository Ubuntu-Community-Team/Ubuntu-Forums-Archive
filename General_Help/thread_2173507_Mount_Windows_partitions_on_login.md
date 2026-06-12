---
title: "Mount Windows partitions on login?"
date: 2013-09-09
forum: General Help
---

### Post by sal02452 on 2013-09-09
I'm running xubuntu 12.10. My PC has a few Windows partitions. When I log in, I see the Windows partitions in the top-left of my desktop. "OS", "DATA", and "Recovery". When I double-click on the icons, it mounts the partition (/media/sal/DATA, etc.) So all of that works fine. But I keep a lot of my home directory in the DATA partition, and it's inconvenient when I forget to double-click before running stuff. Is there a way to have those partitions automatically mounted when I log in, and remain mounted until I log out?

---

### Post by carl4926 on 2013-09-09
Take a screen of your partitions in Gparted and post it here
And also supply the result of

```
cat /etc/fstab
```

---

### Post by David_Pecot on 2013-09-09
It's not too hard.  You just have to edit your /etc/fstab file.  Make a backup first (!)

This article explains how to do this without knowing the details (I do not have direct experience with this program):
[http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/](http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/)


If you want to be an expert (this is what I do, assuming I didn't add the partitions when I installed my system):
[http://www.go4expert.com/articles/automatically-mounting-partitions-linux-t7416/](http://www.go4expert.com/articles/automatically-mounting-partitions-linux-t7416/)
[http://linuxexpresso.wordpress.com/2010/03/14/mount-partitions-in-terminal-fstab/](http://linuxexpresso.wordpress.com/2010/03/14/mount-partitions-in-terminal-fstab/) (and many similar pages)

---

### Post by oldfred on 2013-09-09
If you post Carl4926's requests we can give specific suggestions on entries to fstab.
Also include this as UUID is the preferred method to mount.
        sudo blkid -c /dev/null -o list
    
Otherwise still another suggestion.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

If not a partition you want to write into, better to mount it but set properties to read only or totally hidden so you do not mount it and accidentally write into it.
      
 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

   Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by sal02452 on 2013-09-10
Thanks. I wasn't sure if editing fstab was still kosher on relatively modern systems that do stuff like detecting your disk's partitions and putting icons for them up on your desktop. (Actually, I think I've been scared to manually edit any system configuration file since about 1999.) :)

---


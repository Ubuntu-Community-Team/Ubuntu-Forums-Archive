---
title: "Cannot change owner of NTFS partition"
date: 2018-01-04
forum: General Help
---

### Post by lymphor on 2018-01-04
Hi,
I recently used **NTFS Configuration Tool** in Ubuntu 16.04 in order to automount a NTFS partition at startup, and now the owner of the mentioned partition is the root. I tried to change it by using Nautilus as root, but it switches back as soon as I change it. Could you please help me? This is my **fstap** output, the partition is **/media/FENICE**:

```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 
#Entry for /dev/sda5 : 
UUID=c6278bc5-5494-40d8-8ee0-54a6801842d8    /    ext4    errors=remount-ro    0    1 
#Entry for /dev/sdb1 : 
UUID=01D29F1808F76C30    /media/FENICE    ntfs-3g    defaults,locale=en_US.UTF-8    0    0  
UUID=f5b4f0c6-cdfd-4376-adb6-685b549cac01    none    swap    sw    0    0
```

Thanks in advance!

---

### Post by oldfred on 2018-01-04
You cannot, its a Windows file system that does not support Linux ownership & permissions.
Your setting in fstab become the default for the entire mount.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 

      
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by TheFu on 2018-01-04
Actually, it is possible to have Unix owners and groups used on NTFS file systems, but it requires maintaining an NTFS-to-Unix user and group mapping file. I've never seen anyone here post how to accomplish it, but I know it is possible, since my work place in the mid-1990s did it.  We had a full-time admin whose primary job was addressing that mapping for about 2K users, but we also used a commercial product.

Let me see if my goolge-fu is up to the task. ... [https://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/](https://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/) explains it and has examples.  [http://manpages.ubuntu.com/manpages/xenial/man8/ntfs-3g.usermap.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ntfs-3g.usermap.8.html) is a tool that might be helpful in making the mapping file.  I haven't tested it. It may still be highly experimental, so I would carefully consider the true end-goal and look for alternative solutions.

But setting the user and group at mount time for NTFS partition in a home environment is really the simple and likely the best choice.

---

### Post by oldfred on 2018-01-04
I did see a post years ago on using NTFS and ownership & permissions.
But one of the knowledgeable users on mounting & permissions was very adamant about not using it, and have not seen much about it since. 
So I do not even suggest it. :)

---

### Post by lymphor on 2018-01-28
Thank you both for your help, oldfred's solution worked perfectly!
In order to delete the content in Trash I had to use the solution of this thread: [https://askubuntu.com/questions/507173/cannot-remove-file-from-trash-that-was-put-there-as-root](https://askubuntu.com/questions/507173/cannot-remove-file-from-trash-that-was-put-there-as-root)
Thank you again very much! :)

---


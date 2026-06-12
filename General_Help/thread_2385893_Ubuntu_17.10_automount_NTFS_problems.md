---
title: "Ubuntu 17.10 automount NTFS problems"
date: 2018-02-26
forum: General Help
---

### Post by SreckoMicic on 2018-02-26
When I setup automount NTFS on startup, using fstab entry or using Disks I have permission problems. I can not Move files to trash and some of the files can not be opened. I tired numerous fstab options, following many Ask Ubuntu questions and answers,  but nothing helps.
On the other hand, if I mount NTFS using Files (clicking on drive), so no automount, everything works fine, I can work with files, can Move them to trash etc...
So what is Files doing that I can not do with fstab, is there any way I an check that?

---

### Post by #&amp;thj^% on 2018-02-26
To get to a solution, Do you have "ntfs-config ntfs-3g" installed?
If Yes then:
```
sudo ntfs-config
```
Will give you visible options.

---

### Post by oldfred on 2018-02-26
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

See post from Morbius1
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by SreckoMicic on 2018-02-27
Thanks following that guide it worked. I think that making that folder as root fixed it ... at least I think so.

---


---
title: "Trouble with mounting errors"
date: 2017-06-22
forum: General Help
---

### Post by sosproject on 2017-06-22
Hy, i'm new and i need help. I have using kubuntu 17 64-bits edition and when i run the command mount -v -t ext4 /dev/sdb $LFS return mount: can't find /dev/sdb2 in /etc/fstab. Any can help me.

---

### Post by deadflowr on 2017-06-22
*Thread moved to **General Help**.*
and I've edited the thread title to something more relevant.

---

### Post by ajgreeny on 2017-06-22
Let's figure out first what partitions you currently have which could possibly be mounted, by running command ```
sudo parted -l
```
We can then suggest appropriate commands to mount individual partitions, but note that partitions are mounted not complete devices, so your command should have been more like ```
sudo mount /dev/sdb2 /mountpoint -v -t ext4
``` where sdb2 is the partition you want to mount and /mountpoint is the folder (see below) where you want to mount it.

Do not mount the partition in a folder that already contains any files or folders or they will become invisible whilst the partition is mounted; use an empty folder in your /home, for example, you can easily make a folder to use for this with command ```
mkdir mount
``` run from your own user terminal.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Habitual on 2017-06-22
Try
```
/usr/bin/udisksctl mount -b /dev/sdb2 /media/<user>/sosproject  > /dev/null 2>&1
``` in terminal.
Possibly, also try
```
/usr/bin/udisksctl mount -b /dev/sdb /media/<user>/sosproject  > /dev/null 2>&1
```
The "/media/<user>/sosproject" is 100% arbitrary and it doesn't even have to exist. ;)
Additionally, there are no chmods or chowns to run using this method. It's all you, if you as the user runs it.
Not likely to serve as perm (ie: /etc/fstab) but will work from [user-ville]("http://manpages.ubuntu.com/manpages/trusty/man1/udisksctl.1.html").

How many partitions on sdb?
Can you run this and paste the reply back here if the above fails somehow? 
Or the other lsblk request is good also. Either or, I reckon.

```
sudo lsblk /dev/sd[a-z] -o model,name,size,fstype,label,uuid,mountpoint
```

I use this method in my backup script
```
#!/bin/bash
cd $HOME ; sync
/usr/bin/udisksctl mount -b /dev/sdc1 /media/jj/external  > /dev/null 2>&1
/usr/bin/ionice -c 3 /usr/bin/rsync -azv  . /media/jj/external/LM17/ --delete # --exclude Videos
/usr/bin/du -sh /home/jj/ /media/jj/external/LM17/
#EOF
```

References:
[http://manpages.ubuntu.com/manpages/trusty/man1/udisksctl.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/udisksctl.1.html)

I hope this helps.

---


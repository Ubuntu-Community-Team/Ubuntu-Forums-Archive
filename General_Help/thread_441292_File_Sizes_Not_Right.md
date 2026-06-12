---
title: "File Sizes Not Right"
date: 2007-05-12
forum: General Help
---

### Post by GuitarRocker2562 on 2007-05-12
I just copied some movies from my NTFS partition to my /home partition. The files are all about 400MB, I am SURE of that, however, ubuntu is reporting some of them as 5GB and I am running out of free space because of this. How do I fix it?

---

### Post by GuitarRocker2562 on 2007-05-12
bump

---

### Post by taurus on 2007-05-12
What's the output of these commands from a terminal?

Applications -> Accessories -> Terminal
```
df -h
ls -la ~
```

---

### Post by GuitarRocker2562 on 2007-05-12
OK, I tried ```
ls -lah /home/ian/Videos/PSP/Regular/
``` on the folder that this happened, this was the result. ```
total 16G
drwxr-xr-x 2 ian ian 4.0K 2007-05-11 23:49 .
drwxr-xr-x 4 ian ian 4.0K 2007-05-11 23:28 ..
-rwxrwxrwx 1 ian ian 5.1K 2007-04-22 08:42 adS216.jpg
-rwxrwxrwx 1 ian ian  76M 2007-04-22 08:42 adS216.mp4
-rwxrwxrwx 1 ian ian 3.8K 2007-04-26 00:53 American Pie 2.jpg
-rwxrwxrwx 1 ian ian 383M 2007-04-26 01:58 American Pie 2.mp4
-rwxrwxrwx 1 ian ian 1.9K 2007-04-25 04:12 American Pie.jpg
-rwxrwxrwx 1 ian ian 2.9G 2007-04-25 04:15 American Pie.mp4
-rwxrwxrwx 1 ian ian 2.2K 2007-04-26 09:26 American Wedding.jpg
-rwxrwxrwx 1 ian ian 2.7G 2007-04-26 10:48 American Wedding.mp4
-rwxrwxrwx 1 ian ian 2.9K 2007-04-27 04:53 Anchorman.jpg
-rwxrwxrwx 1 ian ian 5.4G 2007-04-27 05:00 Anchorman.mp4
-rwxrwxrwx 1 ian ian 5.2K 2007-04-27 09:08 Beerfest.jpg
-rwxrwxrwx 1 ian ian 402M 2007-04-27 09:09 Beerfest.mp4
-rwxrwxrwx 1 ian ian 3.8K 2007-04-23 15:34 The 40 Year Old Virgin.jpg
-rwxrwxrwx 1 ian ian 3.8G 2007-04-23 15:42 The 40 Year Old Virgin.mp4


``` See what I mean. As for ```
df -h
``` I get ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.7G  3.0G  6.2G  33% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  132K  502M   1% /proc/bus/usb
udev                  502M  132K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda5              52G   39G   12G  78% /home
/dev/sda1             7.5G  7.3G  219M  98% /media/sda1
/dev/disk/by-uuid/4478C42778C41A16
                      116G   89G   27G  78% /media/sda2
```

Now, can I get help?

---

### Post by taurus on 2007-05-12
> **GuitarRocker2562 said:**
> OK, I tried ```
ls -lah /home/ian/Videos/PSP/Regular/
``` on the folder that this happened, this was the result. ```
total 16G
drwxr-xr-x 2 ian ian 4.0K 2007-05-11 23:49 .
drwxr-xr-x 4 ian ian 4.0K 2007-05-11 23:28 ..
-rwxrwxrwx 1 ian ian 5.1K 2007-04-22 08:42 adS216.jpg
-rwxrwxrwx 1 ian ian  76M 2007-04-22 08:42 adS216.mp4
-rwxrwxrwx 1 ian ian 3.8K 2007-04-26 00:53 American Pie 2.jpg
-rwxrwxrwx 1 ian ian 383M 2007-04-26 01:58 American Pie 2.mp4
-rwxrwxrwx 1 ian ian 1.9K 2007-04-25 04:12 American Pie.jpg
**[COLOR="Red"]-rwxrwxrwx 1 ian ian 2.9G 2007-04-25 04:15 American Pie.mp4[/COLOR]**
-rwxrwxrwx 1 ian ian 2.2K 2007-04-26 09:26 American Wedding.jpg
**[COLOR="Red"]-rwxrwxrwx 1 ian ian 2.7G 2007-04-26 10:48 American Wedding.mp4[/COLOR]**
-rwxrwxrwx 1 ian ian 2.9K 2007-04-27 04:53 Anchorman.jpg
**[COLOR="Red"]-rwxrwxrwx 1 ian ian 5.4G 2007-04-27 05:00 Anchorman.mp4[/COLOR]**
-rwxrwxrwx 1 ian ian 5.2K 2007-04-27 09:08 Beerfest.jpg
-rwxrwxrwx 1 ian ian 402M 2007-04-27 09:09 Beerfest.mp4
-rwxrwxrwx 1 ian ian 3.8K 2007-04-23 15:34 The 40 Year Old Virgin.jpg
**[COLOR="Red"]-rwxrwxrwx 1 ian ian 3.8G 2007-04-23 15:42 The 40 Year Old Virgin.mp4[/COLOR]**


```

You have some large files in your $HOME directory.

```
du -h ~
```
would tell you which directory is taking up most of the space but you should already know which one.

---

### Post by GuitarRocker2562 on 2007-05-12
Well, that is not my home directory, it is the big folder. And my problem is that the files that say 2.0GB+ are only about 400MB, how do I get ubuntu to reconize the actual size?

---

### Post by GuitarRocker2562 on 2007-05-13
anyone?

---

### Post by mdurham on 2007-05-13
Which OS?
How (which program) did you copy the files?
How about an:   ls -la <NTFS folder> to see the source files.
I don't have any solution, but it's very interesting!
Cheers, Mike

---


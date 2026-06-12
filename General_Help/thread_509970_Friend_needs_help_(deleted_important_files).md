---
title: "Friend needs help (deleted important files)"
date: 2007-07-26
forum: General Help
---

### Post by Albertahawk on 2007-07-26
My friend was playing around with his root account and ended up deleting several of the objects in /media, but hes not sure which ones, (im at his house right now, screenshot below)

Is there anyway he can get them back or will ubuntu just pick back up on them next boot (given he deleted the cd/hard drives)

He has:

Two (linux) formatted HD's (I got HD two back by mounting it again, HD1 (Ubuntu install is functioning but he hasnt rebooted)
One Cd drive [This is showing up as broken link now]
One DVD drive
One floppy drive

[[IMG]http://img120.imageshack.us/img120/7223/screenshotvn6.th.png[/IMG]](http://img120.imageshack.us/my.php?image=screenshotvn6.png)

---

### Post by buixuanduong1983 on 2007-07-26
First try:

gedit /etc/fstab

to find out which partition he has. Then can see which folder he has delete.

---

### Post by kevinlyfellow on 2007-07-26
Yeah, it sounds like he just deleted the folders and not the contents.  To remedy, 
```
sudo mkdir *foldername*
```

---


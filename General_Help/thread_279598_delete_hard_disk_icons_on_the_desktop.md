---
title: "delete hard disk icons on the desktop"
date: 2006-10-18
forum: General Help
---

### Post by flapane on 2006-10-18
Yesterday I updated to kde 3.5.5 and all the hard disk icons appeared on the desktop. 
How to eliminate them? I don't need 'em there

[[IMG]http://img139.imageshack.us/img139/8461/sk28ve0.th.jpg[/IMG]](http://img139.imageshack.us/img139/8461/sk28ve0.jpg)

---

### Post by Arby on 2006-10-18
Just delete them. Click on them or drag around them and hit delete, or right click and choose delete

dead easy:)

---

### Post by maheshjagadeesan on 2006-10-18
> **flapane said:**
> Yesterday I updated to kde 3.5.5 and all the hard disk icons appeared on the desktop. 
How to eliminate them? I don't need 'em there

[[IMG]http://img139.imageshack.us/img139/8461/sk28ve0.th.jpg[/IMG]](http://img139.imageshack.us/img139/8461/sk28ve0.jpg)
Hmmm, I think you may want to take a look at 
[https://wiki.ubuntu.com/MediaOnDesktop](https://wiki.ubuntu.com/MediaOnDesktop)

---

### Post by maheshjagadeesan on 2006-10-18
> **flapane said:**
> Yesterday I updated to kde 3.5.5 and all the hard disk icons appeared on the desktop. 
How to eliminate them? I don't need 'em there

[[IMG]http://img139.imageshack.us/img139/8461/sk28ve0.th.jpg[/IMG]](http://img139.imageshack.us/img139/8461/sk28ve0.jpg)
Oops, I also meant to say, after reading that, you have to do the following to remove it from the desktop:
a. Open Konqueror, and create folders under /mnt. You should create as many folders as there are partitions on your desktop.
b. Go to K-Menu->System Settings->Disk and Filesystems->Administrator mode
c. For each partition that appears on your desktop, you'll need to change the mount point (click on 'Modify') after selecting your partition.

Now, the next time you restart your system, the icons shouldn't appear!

---

### Post by kr152ta on 2007-04-22
Check the following:
[https://answers.launchpad.net/ubuntu/+question/2625](https://answers.launchpad.net/ubuntu/+question/2625)

Press ALT+F2 run gconf-editor
Navigate on the left to Apps --> Nautilus --> Desktop and you will find an option called "volumes_visible". Switch that off.

This is so easy :)
Krisz

---


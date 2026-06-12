---
title: "GVfs warning"
date: 2021-09-05
forum: General Help
---

### Post by robert48 on 2021-09-05
Hi
I'm getting an error message when editing fstab:-

bob@bob-desktop:~$ ```
sudo gedit /etc/fstab
```
[sudo] password for bob: 

> (gedit:10394): Tepl-WARNING **: 15:58:59.776: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.


I have just added a new SSD for backups, mounted on /mnt, chown'd and it all works fine using Duplicity.

I appear to have messed up fstab in some way but other than the error message everything appears to be working normally.

What have I done wrong please?

---

### Post by mikewhatever on 2021-09-05
I thought <sudo gedit> stopped working a long time ago, along with any other graphical program. You might want to try <sudo nano>, or, if gedit is a must, then <pkexec gedit>.

---

### Post by robert48 on 2021-09-05
```
sudo nano /etc/fstab
```works for me

```
pkexec gedit /etc/fstab
```did not work for me and gave the following error:-

Unable to init server: Could not connect: Connection refused

(gedit:14095): Gtk-WARNING **: 22:10:00.130: cannot open display: 
bob@bob-desktop:~$

I am still puzzled with the GVfs warning in my initial post. gedit was working fine up until I added a new drive. I'm using 20.04 Desktop 64bit from a fresh install a month or so ago.

---


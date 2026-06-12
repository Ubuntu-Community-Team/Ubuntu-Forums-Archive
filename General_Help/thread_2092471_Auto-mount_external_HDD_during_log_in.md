---
title: "Auto-mount external HDD during log in?"
date: 2012-12-07
forum: General Help
---

### Post by eldobeldo on 2012-12-07
Hi, 

Neither of my hdd auto-mounts after log in. I have my dropbox folder on my secondary external HDD. Unless it is mounted, it won't sync my files. It gets really frustrating because I have to mount the hdd, then start up dropbox. 

Is there any way to get it to auto-mount during set up? 

I have already used gconf-editor and double checked that the auto-mount option checked. 

Any help would be much appreciated. Thank you. 

p.s. I am on 12.10 Ubuntu-Gnome Remix

---

### Post by Kirk Schnable on 2012-12-07
If the drive is always plugged in, you might consider making an fstab entry to mount it automatically at boot. There is some general documentation on this here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Myself or someone else here can help you with the specifics if you choose to go this route.

---

### Post by oldfred on 2012-12-08
Welcome to the forums.

Is it auto-mounting but under a different mount point than that your want?

Sometimes just adding a label so the it mounts as /media/label rather than the default of /media/uuid or sometimes just the size.

You can easily set labels with Disk Utility, gparted or depending on format different command line utilities. I normally use Disk Utility.

---


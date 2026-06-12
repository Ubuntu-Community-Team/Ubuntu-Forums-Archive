---
title: "Auto mount internal hard drives"
date: 2007-09-13
forum: General Help
---

### Post by Danyl on 2007-09-13
Hi all

I've followed this guide: [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux") to try and get 2 internal hard drives to auto mount when I start up.

Basically I have 3 HD's, one 10 gig (with Ubuntu on it), one 80gig one with my music ogg's on it and a 200 gig which is yet to be used.

Now when I boot up it appears to be mounting the 80 gig drive (as when I open rhythmbox it finds the directory I've told it to look for and hence finds my music collection) however the icon for the drive doesn't show anywhere! Its not on the desktop and its not in Computer. It used to appear under Computer and I'd right click and mount it but now after following this guide, the icon has disappeared!

How do I get it back?

---

### Post by rivalarrival on 2007-09-14
Your drive is now available (if you followed that guide to the letter) under Filesystem > /storage.

fstab mounts your drives/partitions at the mount point you specify. To access them, you simply browse to that folder from the filesystem. 

You don't have to mount it to /storage...  For instance, you could mount it in your home folder (probably /home/Danyl- if Danyl were your Ubuntu username) by making a directory  within your home directory and changing the fstab entry to point to it.
```
mkdir /home/Danyl/music 
```

then change your fstab entry to read:
```
/dev/hda5 /home/Danyl/music ext3 defaults 0 0
```
instead of 
```
/dev/hda5 /storage ext3 defaults 0 0
```

(Replace hda5 with your harddrive's designation and Danyl with your ubuntu username, of course)

---

### Post by Danyl on 2007-09-17
Cheers rival, will give it a try.

---


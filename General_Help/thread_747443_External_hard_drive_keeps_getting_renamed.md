---
title: "External hard drive keeps getting renamed"
date: 2008-04-06
forum: General Help
---

### Post by snkngshps on 2008-04-06
I have all of my music and video on my external hard drive. I use Amarok as my music player and set my music folder on my external drive as the folder to check for my music files.. well after a couple of days all of a sudden it wasn't finding anything.. After some search I found out that somehow an underscore got added to the name of my external drive. So I cleared my library and reset the shared folder.. After another few days, another underscore was added. Now there is a third added. I don't want to have to keep resetting my library.

I've tried to rename the folder back to it's original name with the sudo mv command but it tells me I can't because "the device or resource is busy". 

Another weird aspect is that the drive sitting on my desktop has no underscores, but when I click to open it it has underscores listed in the folder address.

Any ideas as to why this is happening and how I can stop it?

---

### Post by noynac on 2008-04-06
This is a known issue. Current threads on this topic include:

[http://ubuntuforums.org/showthread.php?t=744469](http://ubuntuforums.org/showthread.php?t=744469)

[http://ubuntuforums.org/showthread.php?t=745236&highlight=underscore](http://ubuntuforums.org/showthread.php?t=745236&highlight=underscore)

A launchpad bug report is at:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/101845](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/101845)

There are a few workarounds--otherwise we have to wait for a fix.

---

### Post by snkngshps on 2008-04-07
Thank you. I was able to get a good workaround.

---


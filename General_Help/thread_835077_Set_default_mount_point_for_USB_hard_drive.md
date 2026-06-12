---
title: "Set default mount point for USB hard drive"
date: 2008-06-20
forum: General Help
---

### Post by rockin_goliath on 2008-06-20
I have all of my music on my Western Digital USB hard drive, and have Rhythmbox set to look for music in that folder. However, sometimes when I eject the USB hard drive and plug it back in later, the mount point changes, say, from /media/disk to /media/disk-1. Thus, Rhythmbox is no longer able to find my music, and I have to rebuild my library. Is there a way to set a default mount point for the USB drive, such as /media/WD-USB, so that Rhythmbox is always looking in the same place for my music files? 

Nautilus has some option tabs where it looks like you can set a mount point, but I'm not sure whether to use the "Volume" tab or the "Drive" tab. What is the difference?

---

### Post by justleen on 2008-06-20
yes, there is.

the udev deamon handles the mounting of the drives. you can create a new rule in  /etc/udev/rules.d quite easily, to ensure that one particular drive is always mounted on a certain mount point..

---

### Post by rockin_goliath on 2008-06-20
Thanks for the quick reply Justleen. 

I'd rather avoid going into text files to accomplish this. Is there a way to do this from the Properties window when I right click on the drive icon on my desktop? I just tried editing the mount point in the "Volume" tab, but then I was unable to mount it at all. I think it was because I put a "-" in the name, and also didn't fill in any of the other options.

---

### Post by kpkeerthi on 2008-06-20
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Change the Volume label to WD-USB using the above guide. Next time, when ubuntu mounts it automatically, it will do so in /media/WD-USB

---

### Post by rockin_goliath on 2008-06-20
I've figured it out, but in doing so I think I've also encountered a bug in Nautilus. All you have to do it right click on the drive icon on the desktop and click Properties, go to the "Volume" tab, and under settings type the desired mount point under /media. This screwed me up the first time, because you are not supposed to enter the entire path, just the name of the folder you want it to be under /media. So instead of /media/WD-USB just type WD-USB. This gui really needs to be reworked to make it easier to understand.

This will do exactly what I want it to do, but now whenever I unmount the drive, it returns an error "Cannot unmount volume: Cannot remove directory." I assume this means it can't remove the WD-USB directory that it is now creating, but the directory is, in fact, removed and the drive is unmounted. I shall file a big against Nautilus for this.

---


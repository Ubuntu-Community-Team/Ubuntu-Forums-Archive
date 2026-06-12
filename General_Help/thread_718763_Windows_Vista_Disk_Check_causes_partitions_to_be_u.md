---
title: "Windows Vista Disk Check causes partitions to be unmounted"
date: 2008-03-08
forum: General Help
---

### Post by SlickTheNick on 2008-03-08
So I recently made the switch over to ubuntu, hopefully for good. Damn tired of using vista. I keep vista though because I use it for certian games that either dont work or dont work very well on wine.

Anyways, everytime I booted up into vista, it wants to do a disk check. I always just skip it cause I just knew it was gonna mess something up on linux, but my friend was using my laptop, and he didnt skip it.

Basically, ubuntu cant seem to mount the vista partition or the partition where I keep all my files on.

I looked around already and cant seem to find anyone else who has had this problem (there probably is though), so ya, help is greatly appreciated

*note - on gparted, the vista and data partitions have a exclamation mark by their names, when I view properties it says "Unable to read the contents of this filesystem!"

---

### Post by boeing777 on 2008-03-08
hope this helps:

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

### Post by SlickTheNick on 2008-03-08
ok thanks, one question though

> To mount FAT partition type command:# sudo mkdir -p /media/d
# sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/hda1 /media/d

so if its a ntfs filesystem, would i type vntfs?

also, whats with the /media/d part? The article doesnt make it very clear what that even means

thanks again

---

### Post by dcstar on 2008-03-08
> **SlickTheNick said:**
> ok thanks, one question though



so if its a ntfs filesystem, would i type vntfs?

also, whats with the /media/d part? The article doesnt make it very clear what that even means

thanks again

1: No.

2: You have to mount filesystems to a **mount point**, "/media/d" is an arbitrary mount point that the instructions use.

---

### Post by SlickTheNick on 2008-03-08
ok, so would I just type ntfs then?

and as for the mount point, what should I set it as then? The partition I want to mount is /dev/sda5 if that helps.

Sorry if im being a pain, im still noob with linux :p

---


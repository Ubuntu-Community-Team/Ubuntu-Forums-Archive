---
title: "Stop Install icon from regenerating on persistent USB"
date: 2012-10-29
forum: General Help
---

### Post by bgalfond on 2012-10-29
Title says really, I have a USB persistent install using a casper-rw partition.  Everything works great, persistence works perfectly except there seems to be some process that generates the install icon on my desktop every time I boot.  Any suggestions on how to prevent the icon from showing up?

Thanks!

32 bit Ubuntu 12.04 (GNOME)
Installed to USB with YUMI, casper-rw ext4 partition with working persistence.

---

### Post by Ms. Daisy on 2012-10-29
It's mounted on the desktop. That means you can unmount it using the umount command but it won't be persistent. You'll have to edit the fstab file to permanently remove it. ```
gksudo gedit /etc/fstab
``` You'll want to look for the line that says "installer" somewhere in it. I would recommend commenting it out (with # in front of the line) rather than deleting it.

**EDIT: If you're not familiar with this, I recommend  you post the /etc/fstab file here so I can tell you precisely what to do.**

Some documentation for you: 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts)
You're essentially reversing this.

Here's an introduction to mounting & unmounting if you're unfamiliar:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by bgalfond on 2012-10-30
Ok, I see how it works now.  I ended up just writing a simple script to delete the icon on boot.  I want to try and avoid removing/altering ubiquity too much so that I can still use it to install to a hard drive when needed.

That was some good reading though, next time I will go for your more elegant approach.

---


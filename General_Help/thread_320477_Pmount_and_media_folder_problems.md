---
title: "Pmount and media folder problems"
date: 2006-12-17
forum: General Help
---

### Post by jensdanne on 2006-12-17
Hi,
I just encrypted my external USB Drive with LUKS, and was now trying to mount the thing with pmount.

Pmount so far works, BUT the created folder in /media is still owned by root:root and not accessible for me as a normal user.

Checking with -d option shows, that the mount line is properly executed, my user is memeber of group "plugdev", but the created directory still gets root:root ownership...

So, any ideas?

---

### Post by taurus on 2006-12-17
Is it ntfs filesystem?

---

### Post by jensdanne on 2006-12-17
no, ext3 formatted.

---

### Post by taurus on 2006-12-17
Where do you mount it to, mount point, because you can change the permissions with chmod command...

```
sudo chmod -R 777 **mountpoint**
```

---

### Post by jensdanne on 2006-12-17
I let pmount mount the device to the /media folder, and I use a nonexistent directory for this (e.g. data-mobil). And of course can I still set permissions with chmod and chown, BUT I should not have to do this, because pmount allows USERS to mount devices and then the device should be readable BY the USER (preferrably WRITEABLE) too.
Is this a udev problem? Or is pmount doing something wrong?

---

### Post by taurus on 2006-12-17
I am not sure whether it is such a good idea to mount it to /media!  If it mounts to /media/data-mobil, then it's find...  Your CD-ROM is supposed to be mounted to /media/cdrom0 so what happens when you insert your CD in?  And so does your USB memory stick, /media/usbstick!  

Therefore, it is a good idea to create a mount point under /media and mount your harddrive there.  And if you plan to mount it each time you boot Ubuntu, then you should create an entry in /etc/fstab for it...

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by jensdanne on 2006-12-17
Dude,

read up on pmount please. It uses /media as a hardcoded directory. And i don't want the disk to be mounted all the time. Just when I plug the USB drive in, the it should get mounted. And that's not done with fstab.

---

### Post by taurus on 2006-12-17
Okay, I will read up on pmount so good luck then...

---

### Post by jensdanne on 2006-12-17
not a problem, mate, I think I found it.
Actually, I still don't know why it doesn't work with ext3 filesystems, but using LUKS and -t vfat, the disk can be mounted normally...
I will continue to investigate this.

---


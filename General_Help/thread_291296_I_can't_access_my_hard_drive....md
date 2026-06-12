---
title: "I can't access my hard drive..."
date: 2006-11-02
forum: General Help
---

### Post by Red Samurai on 2006-11-02
I decided to try Ubuntu recently, and I'm currently running it from a CD. Everything seems fine, except that I can't access my hard drive. When I try, I get this error:

"Unable to mount the selected volume
error: device /dev/sda2 is not removable
error: could not execute pmount"

Does anyone know how I can fix this?

Thanks in advance.

---

### Post by podunk on 2006-11-02
You have to mount the drive to a mount point on your virtual file system. I followed these instructions to do that. First:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

if you want to write to the disk:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_remount_.2Fetc.2Ffstab_without_rebooting](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_remount_.2Fetc.2Ffstab_without_rebooting)

May I offer the comment that unless you are backing up or recovering your Windows drive mounting it pretty well defeats the purpose of the Live CD which is to try out Ubuntu without placing your Windows install at risk.

I'd be very hesitant to write to my windows drive while they were mounted on a virtual disk/file system.

---

### Post by Red Samurai on 2006-11-02
Thanks man. Thing is, my XP is pretty messed up at the moment, and I'm just trying to backup any important files before I format the hard drive.

---

### Post by podunk on 2006-11-02
Linux will back up windows much better than windows will! :) If you have a external USB drive go ahead and mount your partition, then plug in the usb drive, and if the windows partition is readable it's quick and easy to copy files over.

If you can't read the windows drive try this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Red Samurai on 2006-11-02
I've mounted the hard drive, and I can access files, but I can only read them. How do I get write permission so I can move files around?

Edit: Actually, scratch that, I can move files to USB devices, and I think that's all I need to be able to do.

---

### Post by Red Samurai on 2006-11-04
Sorry to bother you again, but I want to know how I can write to the disk (I need to rename some drivers, long story). I checked the second link you posted in your first post, but it wasn't helpful. Could you explain it please?

Thanks.

---

### Post by xmastree on 2006-11-04
Unfortunately, if the disk is NTFS you're stuck. Can you run windows at all, and mount the USB drive? That could be your best bet.

---

### Post by Red Samurai on 2006-11-04
Nope, can't run Windows... Not even in safe mode now. I think I might try a repair installation or something...

---

### Post by ehird on 2006-11-04
Simply wrong! You are not stuck, check the wiki.

---

### Post by Red Samurai on 2006-11-04
So, is it possible to enable write permission? I need someone to guide me through the process, I'm kinda confused.

---


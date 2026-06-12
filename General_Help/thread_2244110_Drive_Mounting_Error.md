---
title: "Drive Mounting Error"
date: 2014-09-13
forum: General Help
---

### Post by mark165 on 2014-09-13
So a few days ago i was playing Minecraft in Windows 8. Suddenly my computer crashed and i went to boot it up again. When i booted up my pc again, i got what is known as "the black screen of death", my screen was black with a blinking underscore. I didn't backup any files so i installed ubuntu on my 1tb drive. So i wanted to put some important files on my Ubuntu install, but when i tried to access my drive, it said the following error. Please help me!!!!
Error mounting /dev/sdb1 at /media/mark/22A05452A0542F13: Command-line 
`mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/
dev/sdb1" "/media/mark/22A05452A0542F13"' exited with non-zero exit status 
14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.



I know it said Please resume and shutdown Windows fully but how can i do that if i can't even go into windows?

---

### Post by yancek on 2014-09-13
Use the Repair option on the windows installation DVD.  Since you just installed Ubuntu to backup files, you could also use the Recovery CD you created when you first booted windows 8.

---

### Post by mark165 on 2014-09-13
Uh.... my kid sort of killed that dvd.

---

### Post by yancek on 2014-09-13
Since the problem is a windows problem, I would think you would have better luck finding a solution at a windows forum or the micrsoft site.  

[http://www.eightforums.com/](http://www.eightforums.com/)

[http://support.microsoft.com/product/windows/windows-8-1](http://support.microsoft.com/product/windows/windows-8-1)

---

### Post by mark165 on 2014-09-14
No, what im looking for is a way to access my windows hard drive.through linux cause I cant even boot windows and I have important files on it.

---

### Post by yancek on 2014-09-14
The reason I posted the two links above was so that you could either do a search or post there about your problem, unable to boot your windows version.  I don't use windows but I would think there must be some software for windows available to try to repair the filesystem.  If you can't mount the partition from Ubuntu, you can't access the files.

---

### Post by mark165 on 2014-09-14
Nevermind somehow it magically was able to mount the drive partition thanks for the help though.

---

### Post by mark165 on 2014-09-14
Now how do I mark this as solved sorry im a noob at forums and stuff

---


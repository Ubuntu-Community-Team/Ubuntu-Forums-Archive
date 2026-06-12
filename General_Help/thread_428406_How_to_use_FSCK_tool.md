---
title: "How to use FSCK tool"
date: 2007-04-30
forum: General Help
---

### Post by Blueshift on 2007-04-30
I'm having trouble, figuring out how to use the fsck tool to check my hard disk for error. I am aware that I have to unmount the file system to check it, but the only way to do that is to engage Ubuntu via the live-cd and do the checkup of my hdd from there.. but I cant seem to figure out what command I have to write to get it to check my hard disk.... some help would be much appreciated :)

---

### Post by jocko on 2007-04-30
If it's an ext2 or ext3 file system, this should do it:
If the filesystem is already mounted, unmount it by:
```
sudo umount /dev/hdXY
```
(if it's your / or /home file system you may need to do it from a live cd)
Then start the check by:
```
sudo e2fsck -fpC 0 /dev/hdXY
```the "-f" option will force a check even if the filesystem is marked as clean, "-p" will repair any errors and "-C 0" will give you a progress bar in the terminal.

---

### Post by Blueshift on 2007-05-14
Thank you!

I finally got my HDD checked for errors, but it doesn't say if there are any errors on the disk or what? When its done checking I get a message:

**0.8% not-contiguous** 

What does that mean?

I can't tell if it has repaired anything on the disk, but I have determined that a file of mine is still damaged. Its a video file and when playing it in totem it stops at a certain point every time. I can hear small tick noises from the harddisk.. and then I get an error message from totem: 

**can't  read from the resource.**

Hope someone can help me with this... thanks :)

---


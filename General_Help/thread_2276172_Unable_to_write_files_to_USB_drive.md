---
title: "Unable to write files to USB drive"
date: 2015-04-30
forum: General Help
---

### Post by isurveilu on 2015-04-30
I'm running Ubuntu 14.04.

Basically my problem is I wrote some files on an EXFAT 16 GB USB stick in Ubuntu. Reading and writing to it was not an issue. Later on I wrote some files to it in Windows 7. I go to write some more files to it in Ubuntu and I have no ability to write to it at all. 

Here's what I've tried: 

1. Drive as EXFAT:
Open Nautilus and change permissions in properties - properties didn't change, no write
Open Nautilus as root and change permissions in properties - properties didn't change, no write.

2. Converted drive to NTFS in Windows 7 and:
Checked the option for allowing writing to volumes in ntfs configuration tool. No write.
Open Nautilus and change permissions in properties - properties didn't change, no write
Open Nautilus as root and change permissions in properties - properties didn't change, no write.

This is a big problem for one reason: My parents need to be able to do this graphically. They are seniors and I have to be able to walk them through it. They have both a Windows and a Linux PC. I'd like them to keep that Linux.

As an aside I have a couple NTFS hard drives that go back and forth I've done nothing special with that don't have this issue.

EDIT:

I tried formatting the USB stick as EXT4 and using paragon EXT4 drivers for windows - [http://www.paragon-drivers.com/extfs-windows/](http://www.paragon-drivers.com/extfs-windows/) The solution's not perfect but I'm in touch with their support to hopefully iron out some bugs.

When I created the EXT4 drive, I did it in gparted. Initially, only root can write to them. I manually changed the permissions in nautilus as root so anyone can read and write to it.

I played around with the files in Windows, making sure I can read/write/modify all the files.

I put the USB stick back into the buntu machine and all of my permissions in nautilus  were reset to only allow root to write to the volume.

---

### Post by ajgreeny on 2015-04-30
Was the drive properly removed from Windows before you attached it to the Ubuntu machine, or if it is the same machine for both OSs, was Windows shut down properly?

I don't know Windows 7 nor if it suspends/hibernated as default, but if it does that would mean that an ntfs disk would still be flagged as in use when you tried to use it in Ubuntu.

---

### Post by isurveilu on 2015-04-30
Yup, drive was properly removed. They are separate machines. Neither Windows machine suspends or hibernates. They are either on or off. There's no a new issue, I edited the original post.

---

### Post by ajgreeny on 2015-05-01
I am not sure I can help much more as I no longer run Windows, nor generally remember how to do much using it (XP was my last and I removed that from the disk years ago).

However, having formatted the USB to ext4, and I know nothing about windows ext drivers, you would need to change ownership of the mountpoint of the USB drive in Ubuntu, which will normally be **/media/username/usbname** (not actually **/media/username/usbname** of course, but you will see what it is in the file manager) with command ```
sudo chown username:username /media/user/usbname
``` and, assuming using the ext driver in windows does not make changes to that, you should then be able to read and write to it as user.

---

### Post by isurveilu on 2015-05-05
Sorry for the long reply time.

```
sudo chown username:username /media/user/usbname
```

Definitely worked. Thanks! I can't seem to wrap my head around the way Linux permissions work. If you're aware of any resources that explain it to someone like they're 10 I'd like to read it. I can't seem to find anything like that.


for anyone else reading this thread the paragon drivers above really don't work that well and finding a different solution will save you some headaches.

---


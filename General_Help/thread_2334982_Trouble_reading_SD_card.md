---
title: "Trouble reading SD card"
date: 2016-08-24
forum: General Help
---

### Post by irv on 2016-08-24
I have been using an 128 Gig SD card in my phone for some time now with no problems. I powered off the phone and then put it in my laptop to add some music. My Ubuntu 16.04 would not read the card. This is the error I got.
> Unable to mount 129 GB Volume
Error mounting /dev/sdb1 at /media/irv/9C33-6BBD: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/irv/9C33-6BBD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
The funny part is I can read it on a Windows 10 OS, but it will not work in Ubuntu or Adroid. My phoe will not read it either. I am starting to think it is Linux error seeing Android and Ubuntu are both Linux.
I don't want to reformat it but am not sure what I can do to fix it. I tried gparted, and it sees the drive but can't mount it. I also tried the command line and did a copy paste using the
 ```
sudo mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/irv/9C33-6BBD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat 
```
but it just tells me that 
```
mount: mount point /media/irv/9C33-6BBD exited with non-zero exit status 32: mount: unknown filesystem type exfat does not exist
```
Any help would be appreachated.

---

### Post by Bucky Ball on 2016-08-24
You need to install exfat-utils and exfat-fuse and all should be fine. ;)

You shouldn't need to do anything then. Just shove the 128Gb into the laptop and it should show up and be accessible like any other SD or USB. It's because the larger capacity SDs are generally SXHC (from memory, or the other one) and they need the extra stuff. Have a close look at the card and you should be able to see what type it is (although you might need a magnifying glass!).

---

### Post by irv on 2016-08-24
Okay, I install exfat-utils and exfat-fuse. I didn't know if I needed to restart or not, so I did a reboot. Now it will not even find the SD card when I plug it it.
Then I was thinking how is this going to help with my phone not seeing it?

EDIT: all of a sudden it started to work, I am going to try it in the phone again. Will let you know if it works.

---

### Post by irv on 2016-08-24
I am not sure what is going on with the phone, but It will not see the SD card? It did before I removed it, and I am not sure if Android has a utility to fix this problem. The card can now be seen on Ubuntu and Windows, but not Android. I may have to go on a Android forum.

---

### Post by ajgreeny on 2016-08-24
Apparently some android systems can read exfat and others can't, though it does not seem to be related to android version, more whether or not the hardware manufacturer built in exfat support or not.

See [https://www.avforums.com/threads/will-android-tablets-read-exfat-systems-formatted-on-windows.1809182/](https://www.avforums.com/threads/will-android-tablets-read-exfat-systems-formatted-on-windows.1809182/)

---

### Post by irv on 2016-08-24
I feel a little stupid. It was the SD card slot in the Phone. It was not seeding all the way in. I have everything working now.
Thanks for the help in getting Ubuntu to read the card by installing the right software. I will mark this thread solved.

---

### Post by Bucky Ball on 2016-08-24
No problems, excellent news and thanks for marking the thread solved to help others. ;)

Was a bit confused there reading through your posts as installing the exfat stuff on your machine doesn't change anything at all on the SD card so I was wondering what was going on. :-k :)

---

### Post by irv on 2016-08-25
It did change, it just took awhile. I plugged in the SD before the computer was completely booted up, so it might have been exfat was not even running yet. After waiting until the machine was fully up I plugged in the SD Card and it worked. I am thinking that is what happen.

---


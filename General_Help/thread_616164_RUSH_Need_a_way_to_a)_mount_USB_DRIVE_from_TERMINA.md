---
title: "RUSH: Need a way to a) mount USB DRIVE from TERMINAL -or- b) open locked filesystem"
date: 2007-11-17
forum: General Help
---

### Post by Grafster on 2007-11-17
Run Xubuntu on Acer Travelmate 230.

Quick explanation: Kernel update completely borked X. I can't get it to run despite hours of work.

I now have an hour before a meeting. I DESPERATELY need to get a power presentation off the hard drive before that meeting.

I can boot the laptap to terminal mode.

[U]I need instructions for how to get a USB thumbdrive to mount IN THE TERMINAL. (I have no gui).
[/U]

I also have the Xubuntu CD and can run load the OS (including GUI) normally, but I don't have permissions to the system using the CD, so I can't get to the file. If there's some way to do this easily (which I doubt) then that would also be fine/great/wonderful.

Help, obviously, would be greatly appreciated.

---

### Post by Grafster on 2007-11-17
Plugging in the thumbdrive gets it to light up it says 

[sdb] Assuming drive cache: write through 

fdisk -l
shows the disk is dev/sdb1 and ID 6 System fat16

can I mount it in media/sdb1?

---

### Post by yabbadabbadont on 2007-11-17
Edit: you're psychic...  :D

Yes, you should be able to mount it.

---

### Post by taurus on 2007-11-17
What filesystem is that USB thumbdrive?  And just so you know, your original kernel is still on your machine when you installed the custom build one _unless_ you removed it.

```
sudo fdisk -l
```

p.s. Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
```
Now, you can just copy whatever you want to /media/sdb1.  And when you are done, unmount it first before you unplug it.

```
sudo umount /media/sdb1
```

---

### Post by CRCarl on 2007-11-17
Do 
```
cd /media
ls
```

insert the USB key, wait a couple of seconds then ls again. You should have a new mount point. cd to it.

---

### Post by yabbadabbadont on 2007-11-17
You may have to create the mountpoint if it doesn't exist.
```
sudo mkdir /media/sdb1
```
Then mount the drive
```
sudo mount /dev/sdb1 /media/sdb1
```
You might need to use the "-t vfat" option if the drive is a normal fat32 format.

---

### Post by Grafster on 2007-11-17
Looks like I got it.
You people are awesome.
Thank you.

---


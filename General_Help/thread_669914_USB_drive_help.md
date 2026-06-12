---
title: "USB drive help"
date: 2008-01-16
forum: General Help
---

### Post by JunsuinoKokoro on 2008-01-16
Some time ago I wanted to see what would happen if I tried to install ubuntu on a usb drive. To say the least, I am now trying to wipe the drive clean (delete the partitions) and start fresh with a normal usb storage drive.

The usb drive is supposed to be 8Gb.  Here is a series of screen shots so whoever might help me can fully understand what the situation is:

[IMG]http://img.photobucket.com/albums/v379/JunsuinaKokoro/ubuntu/Screenshot-diskProperties.png[/IMG]

[IMG]http://img.photobucket.com/albums/v379/JunsuinaKokoro/ubuntu/Screenshot--dev-sdb-GParted01.png[/IMG]

[IMG]http://img.photobucket.com/albums/v379/JunsuinaKokoro/ubuntu/Screenshot--dev-sdb-GParted02.png[/IMG]

[IMG]http://img.photobucket.com/albums/v379/JunsuinaKokoro/ubuntu/Screenshot--dev-sdb-GParted03.png[/IMG]

As you can see, I've tried using Gparted, and only two of the three partitions can be deleted. I can not seem to delete the partition with the extended file system, so it would appear that I can not make use of the 376.52Mb that it consumes.

If anyone can advise me on how I can reclaim all of my storage space back, I'd be very grateful.

---

### Post by mathisdermaler on 2008-01-16
*****WARNING: instructions here will erase all the data on the drive you choose!*****

I would use plain ole fdisk myself.  
1) Open a shell

2) change to the root user

3) run fdisk
```

fdisk /dev/xxx

```
(substitute the proper device name in place of xxx)

4) Then type "o" and press ENTER (create a blank partition table)

5) Then type "w" and press ENTER (save your changes to the drive)

---


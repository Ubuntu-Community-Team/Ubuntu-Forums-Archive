---
title: "Automounting a specific external USB drive"
date: 2017-11-30
forum: General Help
---

### Post by cc1984 on 2017-11-30
I looking for a way to automount a specific USB external drive to a specific directory. I have an external drive with the Ubuntu repos on it and I need it to always mount to a specific directory while all other USB drives simply mount to /media/usb or something. 

I'm familiar with mounting drives manually and setting the system to automount all USB drives to a directory but wondering if there is a way to identify one specific drive and have it always mount somewhere else.

---

### Post by timothylegg on 2017-12-01
Yes, there is a way.  The most famous solution to this problem is using the file  /etc/fstab

Your USB drive's partition has a unique identifier that was created during the formatting process called a UUID.  By creating an fstab entry with the UUID and a mountpoint, the drive will be automatically mounted.

You should be able to find the UUID from your device with this command (away from console - I haven't tested this):

[COLOR=#000000][FONT=Consolas]$ blkid /dev/sda1

[/FONT][/COLOR]then add a line in the fstab file, something similar to this (untested, please refer to man page)

[COLOR=#BB60D5][FONT=&quot]UUID[/FONT][/COLOR][COLOR=#666666][FONT=&quot]=[/FONT][/COLOR][COLOR=#000000][FONT=&quot]03b77228-ed4c-4218-910e-11b9f77c4b46  /my_path/my_drive/ ext4     defaults

provided that your filesystem is ext4.  There may be some variation in this process if the partition is non-ext or a swap partition.  I can only guide you in the right direction of where to look so that you can customize your perfect solution
[/FONT][/COLOR]

---

### Post by leunam12 on 2017-12-01
Check the link below for more information on working with fstab.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by cc1984 on 2017-12-03
Thanks, just what I was looking for!

---


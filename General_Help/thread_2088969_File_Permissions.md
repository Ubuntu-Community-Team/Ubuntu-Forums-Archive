---
title: "File Permissions"
date: 2012-11-27
forum: General Help
---

### Post by JD32 on 2012-11-27
I have a transmission daemon running on my SSH sever and the main HDD was quite small so instead of buying a new HDD i just plugged in an external USB HDD i had laying around. Well i want to download my torrents to the drive. "/media/usb0" After chmod 777'ing the directory i can download to it but for some reason anything i do download to it takes SUDO permission to copy, rename, move etc. I can go in and CHMOD the file and that solves it but is there anyway i can stop from having to do it every time?

---

### Post by JKyleOKC on 2012-11-27
Add something like this to your /etc/fstab file: ```
/dev/sdb1   /media/usb0    vfat     rw,user,noauto,umask=0,uid=1000
```This assumes that you don't already have a "/dev/sdb1" device and that your external drive is formatted as "vfat" so you may need to change these values. The options force read-write permission on the drive, allow you to mount it without having to use sudo, prevent it from interfering with bootup if the drive isn't plugged in, retains full read-write-execute permission for everyone, and finally set your UID (1000 is the normal value for the first account defined) as owner of everything.

I copied that line from my own /etc/fstab, where I added it to provide full access to my thumb drives. As I say above, you may need to change the actual device name and the filesystem type to match your setup. You can find out what yours are by issuing the command "mount" in a terminal window, with the drive plugged in and accessible. This will list all mounted devices, and you can copy off the device name and type from that list.

---


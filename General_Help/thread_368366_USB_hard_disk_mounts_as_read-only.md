---
title: "USB hard disk mounts as read-only"
date: 2007-02-23
forum: General Help
---

### Post by ainsworth on 2007-02-23
I have an ordinary hard disk in an external caddy which everytime is connected mounts automatically, however readonly. If I right click on the icon on desktop, go to permissions I'm unable to change to "Create and delete files", the following error comes up:
 "Couldn't change the permissions of "Andrew" because it is on a read-only disk"

What am I doing wrong? Thanks.

---

### Post by bash on 2007-02-23
what filesystem is on the Harddrive? 

If its ext3 do the following:
1. Open a terminal
2. Type "sudo chown [your username] /media/nameoftheusbdrive". Press enter
3. Type "sudo chgrp [your username] /media/nameoftheusbdrive". Press enter again.
4. Be a happy monkey

Note that you have to type your username without the []

---

### Post by ainsworth on 2007-02-23
sorry, I knew there was something I forgot to mention. Its ntfs, from an old windows machine.

---

### Post by yme on 2007-02-24
> **ubun-two said:**
> what filesystem is on the Harddrive? 

If its ext3 do the following:
1. Open a terminal
2. Type "sudo chown [your username] /media/nameoftheusbdrive". Press enter
3. Type "sudo chgrp [your username] /media/nameoftheusbdrive". Press enter again.
4. Be a happy monkey

Note that you have to type your username without the []

I've exactly the same problem with an external USB harddrive that I bought formatted (so I presume is FAT32). 

I tried these instructions and got the following feedback:

yme@yme:~$ sudo chown yme /media/SPD5100CC
Password:
chown: changing ownership of `/media/SPD5100CC': Read-only file system
yme@yme:~$ sudo chgrp yme /media/SPD5100CC
chgrp: changing group of `/media/SPD5100CC': Read-only file system
mihail@SpectrumNet:~$

The drive is still read only when I try to do anything!

I have a similar problem when logged in as user that files I have copied to the machine from the drive and then move to the trash can't be deleted. 

me!

---

### Post by SonicSteve on 2007-02-24
Hi guys,
I have a 20gb usb drive, it automounts as read only.
However if I eject it, then run this command;
sudo mount -t ntfs-3g /dev/sda5 /mnt/usb20
It works!!
I haven't figured out how to automount it using ntfs-3g though.

Keep in mind I first created the mnt/usb20 folder to mount into. Your disk will likely have a different dev listing, perhaps sda4 or.... I'm not a linux guru yet. 
I found that mine was dev/sda5 by using administration> device manager. I found the volume in the list then clicked the advanced tab. The block.device value on the right is the dev listing. 
Sorry if you know this, I just wanted to explain abit since this will be searched by eveyone.

---

### Post by yme on 2007-02-25
> **ainsworth said:**
>  "Couldn't change the permissions of "Andrew" because it is on a read-only disk". What am I doing wrong? Thanks.

I've searched around and apparently NTFS filesystems are automatically mounted as read-only in Ubuntu. It takes some jiggery pokery (which might not be safe) to get them fully working:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

I just switched to Ubuntu from Fedora this week and my first impressions is that Ubuntu is vastly better. This is the first major downside I've found. 

me!

---

### Post by ofek on 2007-02-25
Nice to see new linux users helping other new linux users.
As for the safety of writing to ntfs I could say ntfs-3g is stable enough for day to day use. You shouldn't worry about it just follow the instructions and u should do fine.

---

### Post by SonicSteve on 2007-02-26
> **yme said:**
> I've searched around and apparently NTFS filesystems are automatically mounted as read-only in Ubuntu. It takes some jiggery pokery (which might not be safe) to get them fully working:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

I just switched to Ubuntu from Fedora this week and my first impressions is that Ubuntu is vastly better. This is the first major downside I've found. 

me!

This ntfs-3g config trick worked brilliantly!!,
I commented out the fstab line that I originally made. Used the Ntfs config, put a checkmark in the allow external write box. And voila.
This is the fix I was trying to find earlier.

---

### Post by Mujaheiden on 2007-08-27
Thanks!
I opened my mtab to find the location where the USB disk mounted ($nano /etc/mtab) and then I found out it was actually assuming it was
 > /dev/sdf1 /media/disk ntfs rw,nosuid,nodev,umask=222,utf8 0 0
so then i unmounted it and (had to) force it into ntfs-3g by
> sudo mount -t ntfs-3g /dev/sdf1 /mnt/test -o force
and now Im writing!

---


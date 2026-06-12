---
title: "Disconnecting Samba and CIFS from remote end make nautilus slow"
date: 2007-07-08
forum: General Help
---

### Post by SonicSteve on 2007-07-08
Hi folks,
I put this one in General help because It isn't just a Networking issue.
So here it is;
I have 2 Fiesty Fawn desktop PC's connected via RJ45 100mb/s cabling and a hub/switch. That mini network is  connected into a router via the hub/switch. The router provides IP addressing with DHCP and internet.

I say all that just so you know how things work around here.
One of the computers simply called "ubuntu" is my server, the other computer that I do most of my work on is called "ubuntu-desktop" it's simple but effective.
If I shut down the "ubuntu" computer (the server) Nautilus becomes really slow on the "ubuntu-desktop" computer. If I try to access places>computer or anything that requires using Nautilus it can literally take 30 seconds for it to appear and become usable. Even once it has appeared every action or click can take similar lengths of time. 

If I restart X (ctrl alt bkspc) things return to normal speed and If I restart the sever then use sudo mount -a I get my shares back at full speed also. However if I shutdown the server again it then becomes slow again. 

This only happens when I shutdown the server thus I conclude that somehow disconnecting the Samba shares from the remote server end is somehow effecting nautilus on the desktop side of things. 
In my fstab file I'm using CIFS to mount the shares.
Here is my fstab file contents;

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=5403907d-802c-4b4a-9de7-7176fd5b79cd / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=c4125673-4ac9-4cd8-b990-4e4183a97fb5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/hdd /media/cdrom0 auto, user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda /media/floppy1 auto rw,user,noauto 0 0
/dev/hdb1 /media/westernD ntfs-3g defaults,locale=en_CA.UTF-8 0 0
//ubuntu/UbShr /mnt/UbShr cifs username=*******,password=*********,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//ubuntu/WD20 /mnt/WD20 cifs username=********,password=*********,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


You'll notice that I do have NTFS3g in the mix and keep in mind that the samba mounts are actually on the same line not broken into 2 lines as they appear above.

---

### Post by SonicSteve on 2007-07-16
Well well well,
I've either stumped you all, the thread got pushed to the bottom too much, or none of you have ever seen this before.
I suppose it could be something else also:)
I'm just bumping this back up to see if a bit more exposure might help.

---


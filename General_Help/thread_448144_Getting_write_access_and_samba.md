---
title: "Getting write access and samba"
date: 2007-05-18
forum: General Help
---

### Post by Entity` on 2007-05-18
I am very well pleased with 7.04 and the included support for ntfs drives upon boot.  But my problem is that they are read-only.  I need to get them to give me read and write access so I can store data on them, effectively freeing me from windows except for gaming.  I also need to know how to install and setup samba to share those drives with read and write access over my network.

I am disappointed that I can no longer find the wiki page on how to install a bunch of useful programs.

---

### Post by MontanaMax on 2007-05-21
There are many samba setup guides - I remember using this one the first time I put it in place - [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I remember under Dapper and Edgy I was only able to get write access when I used the /etc/fstab method to mount the drives - just doing it on the fly in the terminal didn't do the trick.

I also found out that samba is being deprecated in favor of a newer windows file sharing protocol, and while I have it up and running at home I don't remember what the heck it's called.... I'll post it back up here when I get back home, along with a snapshot of a working /etc/fstab file.

---

### Post by Entity` on 2007-05-25
Thanks dude, ill keep watch.  Thanks for the link too.

---

### Post by MontanaMax on 2007-05-26
OK - I just did a fresh Feisty install last night, and went the fstab entry method on getting write access to my samba network drives. The /etc/fstab line I used is:

```
//192.168.1.43/backup /mnt/backup        cifs    uid=1000,gid=0,user=USERNAME,pass=PASSWORD,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

So in this case the network resource is at //192.168.1.43/backup  and the local mount point is at /mnt/backup

The file_mode and dir_mode values make the resource writable for all users on the system.

Of course, make sure to replace USERNAME and PASSWORD with the appropriate values. :)

(For those reading this post later but not familiar with this process, you need to add the line into your /etc/fstab file in superuse mode and then trigger an automount to have it connected the first time.)

```
sudo nano /etc/fstab
sudo mount -a
```

Good luck!

---


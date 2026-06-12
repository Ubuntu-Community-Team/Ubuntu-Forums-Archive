---
title: "Ubuntu user permissions"
date: 2013-02-12
forum: General Help
---

### Post by mafi127 on 2013-02-12
I'm running ubuntu 12.04 LTS headless server in my home. I have installed deluge in the server using this guide 
[http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)

I have made a new user in my server:
```
sudo adduser --disabled-password --system --home /var/lib/deluge --gecos "SamRo Deluge server" --group deluge

```

Now the problem starts in here. when flexget add someting to deluge and the file is downloaded to my external hdd then I cant access the file, because the owner of this file is user Deluge and group is Deluge. I cant unrar it, right now I have unrared and modified the files when I do

```
sudo chmod -R 777 *
```

I have now two users in my computer

"Deluge" and other is "seed"

```
seed@MediaServer:/media/2TB/downloads/$ ls -l
total 4
drwxr-xr-x 3 deluge deluge 4096 Feb 12 22:06 Ubuntu 12.04 LTS
```

how can I add edit/delete premission to the files what user Deluge makes so I can allso modifie them. and reverse, that user deluge can copy files to folders what user Seed has ben made.

---

### Post by LewisTM on 2013-02-12
I assume you have some sort of Linux filesystem on your 2 TB drive, like ext4.

I would go for Access Control Lists to enable write permission for both users. 
```
sudo setfacl -R -m seed:rwX,deluge:rwX,default:seed:rwX,default:deluge:rwX /media/2TB/downloads
```
This command will set read+write+executable access to all files for both users. It will also set any newly created files to acquire these permissions by default. You can run **getfacl <file> **to view the ACL permissions. Package **eiciel** provides a nice ACL editor integrated with the Nautilus file properties dialog.

Cheers!

---

### Post by mafi127 on 2013-02-13
Thank you, I wil ltest it :)

---


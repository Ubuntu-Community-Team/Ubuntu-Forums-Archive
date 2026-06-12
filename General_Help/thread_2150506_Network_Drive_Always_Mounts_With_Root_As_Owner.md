---
title: "Network Drive Always Mounts With Root As Owner"
date: 2013-06-01
forum: General Help
---

### Post by UltraAnders on 2013-06-01
I've followed the guide [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") on how to "Mount password protected network folders".
I created the folder /media/rpSeagate, and took ownership. However, each time this drive mounts, root takes ownership so I cannot make any changes.

Here is my line from /etc/fstab:
```
//raspbmc/seagate /media/rpSeagate cifs credentials=/home/anders/.smbcredentials,iocharset=utf8,sec=ntlm 0 0 
```

I'm using Ubuntu 12.04 on my main computer. The drive is an external HDD attached to my Raspberry Pi running Raspbmc. The hard drive is formatted as EXT4. Username Anders on 12.04, username Pi on the RaspberryPi, which is what I'm logging on as to gain access to the network drive (stored in the .smbcredentials file).

Permissions on the 12.04 computer
```
anders@anders-Ubuntu-12:/media$ ls -l
total 10
drwxrwxrwx 15 anders anders 4096 Apr  5 21:29 data
lrwxrwxrwx  1 root   root      7 Oct 10  2012 floppy -> floppy0
drwxr-xr-x  2 root   root   4096 Oct 10  2012 floppy0
dr-x------  3 anders anders   88 Jul  7  2011 FRINGE_SEASON_3_DISC_5
[COLOR="#FF0000"]drwxr-xr-x  1 root   root      0 May 25 21:39 rpSeagate[/COLOR]
```
Permissions on the Raspberry Pi as seen via SSH.
```
pi@raspbmc:/media$ ls -l
total 4
drwxrwxrwx 5 pi pi 4096 May 25 21:39 Seagate
```
How do I stop root from taking ownership when mounting this drive?

---

### Post by 2F4U on 2013-06-01
Try to add uid=anders,gid=users to /etc/fstab mount, so that it reads

```

//raspbmc/seagate /media/rpSeagate cifs credentials=/home/anders/.smbcredentials,uid=anders,gid=users,iocharset=utf8,sec=ntlm 0 0
```

The directory /media/rpSeagate should have the same owner/group privileges.

---

### Post by UltraAnders on 2013-06-01
> **2F4U said:**
> Try to add uid=anders,gid=users to /etc/fstab mount, so that it reads

```

//raspbmc/seagate /media/rpSeagate cifs credentials=/home/anders/.smbcredentials,uid=anders,gid=users,iocharset=utf8,sec=ntlm 0 0
```

The directory /media/rpSeagate should have the same owner/group privileges.Whoop, that's done it. Thank-you so much :) :D

---

### Post by 2F4U on 2013-06-01
No problem, you are welcome.

---


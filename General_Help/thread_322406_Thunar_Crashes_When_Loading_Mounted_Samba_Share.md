---
title: "Thunar Crashes When Loading Mounted Samba Share"
date: 2006-12-20
forum: General Help
---

### Post by shewbox on 2006-12-20
I am running Ubuntu 6.10, and am getting this problem while in XFCE.

I have an extra ubuntu box set up as a print server/backup box.  I have set up this extra box as a place to backup important files, and did so by following the instructions on ubuntuguide.org.  I have the drive mounted on this computer in /home/ben/backup.  I can browse/read/copy just fine from the terminal, but if I try to view the directory in Thunar, it says 'Loading folder contents..' for about 2 seconds, then crashes.

I was planning on having the drive automounted on startup, but since I am getting this error, I am manually mounting the drive like so:

```
sudo smbmount //192.168.1.101/public /home/ben/backup/ -o username=myusername,password=mypassword,uid=100,mask=000
```

Nautilus can view the network drive no problem, but I don't like loading Nautlius in XFCE since it somehow takes over the desktop.  Do I give up on Thunar and only use command line?

---

### Post by dannyboy79 on 2006-12-22
i use xubuntu. the way I mount samba shares is by using xsmbrowser. it's awesome! give it a shot. it's in the repos. not sure if it in multi or univer but it's in one of them. or you could just create bash scripts for mounting samba shares, i did that for a while.

another thing to try is to use cifs instead of smbfs.

---


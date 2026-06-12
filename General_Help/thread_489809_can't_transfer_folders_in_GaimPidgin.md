---
title: "can't transfer folders in Gaim/Pidgin"
date: 2007-07-01
forum: General Help
---

### Post by xjgnsdof on 2007-07-01
I've been looking hard for a way to transfer folders through a chat client because I have two computers (one on wired LAN, the other on a wireless router connected to the wired LAN) and often need to transfer large files between the two.

Is there a chat client that allows for the transfer of folders? I have tried Gaim, Pidgin, and QNext, but none of them work. I've tried installing AIM 5.9 through WINE, and I couldn't even get it to launch.

If it's not possible through chat client, how else can I transfer folders from a wired computer to a wireless one? (and I refuse to compress the files and folders)

---

### Post by tillo on 2007-07-01
```
tar cf directory.tar directory/
```
This doesn't compress anything, it just needs temporarely the same space taken by the whole directory.

If you just want to transfer those files, why don't you use FTP, SSH or nc?
The other day I read about someone wanting to install Windows Live Messenger on Ubuntu because of its Spaces feeds... stop using software meant to serve a specifical service for other services!

---

### Post by xjgnsdof on 2007-07-20
I have two laptops, one connected to a wired network, the other on a wireless network. Can I FTP files between the two? If so, how?

I've installed vsftpd, but I have no clue how to actually use it. Can I use FileZilla on the wireless computer to access files on the wired one? No instructions I've found online make any sense.

---

### Post by strabes on 2007-07-20
[Here's](http://ubuntuforums.org/showthread.php?t=218630%20) a tutorial for setting FTP up between 2 computers. It's really easy.

---

### Post by xjgnsdof on 2007-07-25
I bought a simple wireless broadband router for my other laptop; they are now both connected to the wireless network in my apartment. Will an FTP setup work now?

---


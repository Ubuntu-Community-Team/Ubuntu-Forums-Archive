---
title: "Files only downlaod to /ROOT + wallpaper wont change"
date: 2007-11-16
forum: General Help
---

### Post by shanksd on 2007-11-16
Like the tittle says, whenever I save something off the internet, like a file or picture, it downloads only to /root. Once its there it cant be moved.Also I cant change my desktop wallpaper by simply right clicking on a picture and hitting change desktop background

any help would be great, thanks.

---

### Post by maybeway36 on 2007-11-16
Can you save files to /root at all? You shouldn't be able to unless you're (suprise) root.

---

### Post by taurus on 2007-11-16
How do you download files from the web?  Are you running that program/command as a regular user or as root?

---

### Post by shanksd on 2007-11-16
I log in under my install username.  I dont even know how to log in as root...Maybe somehow the two have tangled up somehow?

---

### Post by Sinisterff on 2007-11-16
> **shanksd said:**
> I log in under my install username.  I dont even know how to log in as root...Maybe somehow the two have tangled up somehow?

What do you use to download?, Does it ask for your password before executing?, I don't know, it could be that you are downloading with sudo or gksudo

Edit: Oh Also, you can move the files with the command  'gksudo nautilus' for now, but it will ask for your password and you'll need to change permissions if you want to modify it

---

### Post by shanksd on 2007-11-16
I just use whatever firefox uses to download. For example; theres a picture I want to save, I right click save image as, and the only place I can save it to is /root, I cant change the directory at alll.  Or a link like an emerald theme, it downloads and says files automaticly are saved to desktop, this dosent happen they all end up in /root and then cant be moved.

---

### Post by taurus on 2007-11-16
What are the output of these commands from a terminal?

```
id
ls -la ~
```

---

### Post by shanksd on 2007-11-17
```

matt@matt-desktop:~$ id
uid=1000(matt) gid=1000(matt) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(matt)
matt@matt-desktop:~$ ls -la ~
total 2116
drwxr-xr-x 40 matt matt    4096 2007-11-17 11:39 .
drwxr-xr-x  3 root root    4096 2007-11-13 13:59 ..
drwxr-xr-x  3 matt matt    4096 2007-11-16 16:16 3d
-rw-r--r--  1 matt matt   10295 2007-11-16 16:16 3d.tar.gz
drwx------  8 matt matt    4096 2007-11-15 23:42 .amsn
drwx------  2 matt matt    4096 2007-11-15 23:41 amsn_received
drwxr-xr-x  8 matt matt    4096 2007-11-13 22:09 .azureus
-rw-------  1 matt matt    3963 2007-11-16 16:17 .bash_history
-rw-r--r--  1 matt matt     220 2007-11-13 13:59 .bash_logout
-rw-r--r--  1 matt matt    2298 2007-11-13 13:59 .bashrc
-rw-r--r--  1 matt matt  119075 2007-11-15 23:12 .bzr.log
drwxr-xr-x  3 matt matt    4096 2007-11-13 21:08 .cache
drwxr-xr-x  4 root root    4096 2007-11-16 16:17 .compiz
drwxr-xr-x  7 matt matt    4096 2007-11-14 11:27 .config
drwxr-xr-x  2 matt matt    4096 2007-11-15 23:16 Desktop
-rw-------  1 matt matt      28 2007-11-17 11:39 .dmrc
drwxr-xr-x  5 matt matt    4096 2007-11-14 11:31 Documents
drwxr-xr-x  4 matt matt    4096 2007-11-14 11:31 .emerald
-rw-------  1 matt matt      16 2007-11-13 21:08 .esd_auth
lrwxrwxrwx  1 matt matt      26 2007-11-13 13:59 Examples -> /usr/share/example-content
-rw-r--r--  1 matt matt 1802743 2007-11-14 11:13 Firefox_wallpaper.png
drwxr-xr-x  2 matt matt    4096 2007-11-14 11:18 .fontconfig
drwx------  4 matt matt    4096 2007-11-17 11:39 .gconf
drwx------  2 matt matt    4096 2007-11-17 11:48 .gconfd
-rw-r-----  1 matt matt       0 2007-11-17 11:40 .gksu.lock
drwxr-xr-x  3 matt matt    4096 2007-11-13 21:08 .gnome
drwx------  9 matt matt    4096 2007-11-15 23:22 .gnome2
drwx------  2 matt matt    4096 2007-11-13 21:08 .gnome2_private
drwxr-xr-x  2 matt matt    4096 2007-11-13 21:08 .gstreamer-0.10
-rw-r--r--  1 matt matt     104 2007-11-17 11:39 .gtk-bookmarks
-rw-r--r--  1 matt matt      86 2007-11-13 21:08 .gtkrc-1.2-gnome2
-rw-------  1 matt matt    1881 2007-11-17 11:39 .ICEauthority
drwxr-xr-x  3 matt matt    4096 2007-11-14 11:22 .icons
drwx------  3 matt matt    4096 2007-11-13 22:09 .kde
drwxr-xr-x  3 matt matt    4096 2007-11-13 21:08 .local
drwx------  3 matt matt    4096 2007-11-13 22:16 .macromedia
drwxr-xr-x  3 matt matt    4096 2007-11-13 22:09 .mcop
-rw-------  1 matt matt      31 2007-11-13 22:09 .mcoprc
drwx------  3 matt matt    4096 2007-11-13 21:08 .metacity
drwx------  3 matt matt    4096 2007-11-13 21:17 .mozilla
drwxr-xr-x  2 matt matt    4096 2007-11-13 22:10 .mplayer
drwxr-xr-x  2 matt matt    4096 2007-11-15 13:16 Music
drwxr-xr-x  3 matt matt    4096 2007-11-15 23:22 .nautilus
drwxr-xr-x  2 matt matt    4096 2007-11-14 11:13 Pictures
-rw-r--r--  1 matt matt     566 2007-11-13 13:59 .profile
drwxr-xr-x  2 matt matt    4096 2007-11-13 21:08 Public
drwxr-xr-x  2 matt matt    4096 2007-11-13 22:09 .qt
-rw-r--r--  1 matt matt    1531 2007-11-16 16:34 .recently-used.xbel
-rw-r--r--  1 matt matt       0 2007-11-13 21:08 .sudo_as_admin_successful
drwxr-xr-x  2 matt matt    4096 2007-11-13 21:08 Templates
drwxr-xr-x  3 matt matt    4096 2007-11-15 22:55 .themes
drwx------  3 matt matt    4096 2007-11-13 21:18 .thumbnails
drwx------  2 matt matt    4096 2007-11-13 21:08 .Trash
drwxr-xr-x  2 matt matt    4096 2007-11-13 21:11 .update-manager-core
drwx------  2 matt matt    4096 2007-11-13 22:08 .update-notifier
drwxr-xr-x  2 matt matt    4096 2007-11-13 21:08 Videos
-rw-------  1 matt matt     180 2007-11-17 11:39 .Xauthority
drwxr-xr-x  2 matt matt    4096 2007-11-13 22:09 .xine
-rw-r--r--  1 matt matt    3108 2007-11-17 11:40 .xsession-errors
]
```

---

### Post by taurus on 2007-11-17
From firefox, look in Edit -> Preferences -> Main -> Downloads -> Save files to and see what does it say there.

---

### Post by shanksd on 2007-11-21
it says files saved to Desktop....

---


---
title: "no xserver-xorg help me"
date: 2007-07-14
forum: General Help
---

### Post by dragonwings on 2007-07-14
what is the command to get and install xserver-xorg 

i can use sudo dpkg-deconfigure xserver-xorg   in recovery mode but not from my desk top terminal is says
                                :Package `xsever-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xsever-xorg is not installed

---

### Post by machoo02 on 2007-07-15
If you are looking at that message from a terminal within Gnome or KDE, then the X server is installed...otherwise you would not have a graphical desktop.  Also, make sure you are spelling 'server' correctly (you have sever a couple of times up there in your example).  Lastly, if you need to install the xserver:```
sudo aptitude install xserver-xorg
```

---

### Post by dragonwings on 2007-07-15
thanks for your help ,but just found that im a dumb *** and forgot to put the r in server

---


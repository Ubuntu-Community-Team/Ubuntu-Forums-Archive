---
title: "couple of xorg.conf files"
date: 2006-10-15
forum: General Help
---

### Post by westcoaster on 2006-10-15
My problem is that i have couple of xorg.conf files in my /etc/X11 is it normal? I have installed nvidia glx with apt-get and i've set resolution 1280x1024,everytime i set other resolution one xorg.conf is more in my etc/X11 it seems weird.I have kubuntu dapper 6.06 LTS.

What do u think about it.Is everythig ok?

---

### Post by aysiu on 2006-10-15
Can you post the output of these commands? ```
cd /etc/X11
ls -l
```

---

### Post by westcoaster on 2006-10-15
here it is 

drwxr-xr-x  2 root root  4096 2006-10-14 22:14 app-defaults
drwxr-xr-x  3 root root     8 2006-08-06 01:58 config
drwxr-xr-x  2 root root    32 2006-08-06 02:01 cursors
-rw-r--r--  1 root root    13 2006-08-06 02:04 default-display-manager
drwxr-xr-x  2 root root    80 2006-10-14 19:23 fluxbox
drwxr-xr-x  6 root root    32 2006-08-06 01:57 fonts
-rw-r--r--  1 root root 17371 2005-12-22 02:00 rgb.txt
lrwxrwxrwx  1 root root    13 2006-10-13 09:57 X -> /usr/bin/Xorg
drwxr-xr-x  2 root root    16 2006-08-06 02:01 xinit
drwxr-xr-x 10 root root  4096 2006-08-06 02:00 xkb
-rw-r--r--  1 root root  5456 2006-10-15 09:54 xorg.conf
-rw-r--r--  1 root root  4738 2006-10-15 00:03 xorg.conf~
-rw-r--r--  1 root root  3985 2006-10-15 00:12 xorg.conf.1
-rw-r--r--  1 root root  5453 2006-10-15 09:54 xorg.conf.2
drwxr-xr-x  2 root root     1 2006-05-28 21:35 Xresources
-rwxr-xr-x  1 root root  3911 2006-03-20 13:29 Xsession
drwxr-xr-x  2 root root    56 2006-08-06 02:04 Xsession.d
-rw-r--r--  1 root root   234 2006-03-20 13:29 Xsession.options
-rw-------  1 root root   614 2006-08-06 01:57 Xwrapper.config

---

### Post by aysiu on 2006-10-15
xorg.conf is normal.
xorg.conf~ is normal, too--that's the automatic backup copy that gets generated when you edit xorg.conf.

I don't know what xorg.conf.1 and xorg.conf.2 are. They appear to have been created roughly the same times as xorg.conf~ and xorg.conf, respectively.

That's weird. I don't know if they do any harm by being there, but I don't know why they're there.

---


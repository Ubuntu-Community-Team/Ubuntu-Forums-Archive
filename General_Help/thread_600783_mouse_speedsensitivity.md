---
title: "mouse speed/sensitivity"
date: 2007-11-02
forum: General Help
---

### Post by denisvv on 2007-11-02
I've been playing the Quake Wars demo a bit and in my quest to get better performance I mucked around with various settings, and I seem to have reset the X11 configuration. Everything works fine, except for the mouse which moves far too slow now. 

The sensitivity slider in the Pref->Mouse does nothing at all now. If I xset the mouse acceleration to around 5x it feels like the right speed but then the mouse moves in 5 pixel increments which is obviously not the solution because I can't aim anything. 

So here's the deal then, whatever the default install config was, it worked. How do I get it back without reinstalling?

PS setting Resolution in xorg.conf yields no result.

---

### Post by bingoUV on 2007-11-02
Did you edit config files? Or did you change settings using GUIs (menus?). Depending on the changes you made, we can work to try to undo them. 

If you only did xset, these changes will not survive a reboot(even a  restart of the X server). In case they survive both, read on.

Are these changes system wide? You can verify by creating another user, and logging in as that user. If his settings are OK, the damage has been done to your account only. If not, system wide misconfiguration has happened.

In case of your system wide screw up, post the output of the following commands, so we can guess which configuration files might have been modified. 

```

ls -ltr /etc | tail -n 25
ls -ltr /etc/X11
date

```

---

### Post by bingoUV on 2007-11-02
One more thing you can try. Backup the /etc/X11/xorg.conf file somewhere safe. Now delete everything from the /etc/X11/xorg.conf file. Now restart X server (ctrl - alt - backspace). 

This would prompt ubuntu to offer to create a xorg.conf for you. Accept the offer, and most likely the default file so created will be to your liking.

---

### Post by denisvv on 2007-11-02
I deleted xorg.conf and restarted gdm, but it just ran normally, except in 800x600. Copied the file back, rebooted, still the same problem. Sensitivity slider does nothing. 

Curiously, there's also a sensitivity slider in Quake Wars and it works (although the maximum is just barely enough).

This is a generic ps2 mouse btw. I vaguely remember having the same problem in FreeBSD, but I have no idea how I fixed it there.

> 
dv@paris:~$ ls -ltr /etc | tail -n 25
drwxr-xr-x  3 root root      4096 2007-10-30 15:29 mysql
-rw-r--r--  1 root root       921 2007-10-31 14:20 blkid.tab.old
drwxr-xr-x  2 root root      4096 2007-11-01 09:06 modutils
drwxr-xr-x  3 root root      4096 2007-11-01 09:06 modprobe.d
drwxr-xr-x  2 root root      4096 2007-11-01 09:06 default
drwxr-xr-x  2 root root      4096 2007-11-01 09:06 rc5.d
drwxr-xr-x  2 root root      4096 2007-11-01 09:06 rc4.d
drwxr-xr-x  2 root root      4096 2007-11-01 09:06 rc3.d
drwxr-xr-x  2 root root      4096 2007-11-01 09:06 rc1.d
drwxr-xr-x  2 root root     12288 2007-11-01 09:06 brltty
drwxr-xr-x  6 root root      4096 2007-11-01 09:06 xdg
drwxr-xr-x  2 root root      4096 2007-11-01 09:07 skel
drwxr-xr-x  2 root root      4096 2007-11-01 09:07 rcS.d
drwxr-xr-x  2 root root     12288 2007-11-01 09:07 init.d
drwxr-xr-x  2 root root      4096 2007-11-01 09:07 menu-methods
drwxr-xr-x  2 root root      4096 2007-11-01 09:07 pam.d
drwxr-xr-x  3 root root      4096 2007-11-01 09:08 kde3
-rw-r--r--  1 root root       921 2007-11-01 09:08 blkid.tab
-rw-r--r--  1 root root     70854 2007-11-01 10:04 ld.so.cache
drwxr-xr-x  2 root root     12288 2007-11-01 10:04 alternatives
drwxr-xr-x 18 root root      4096 2007-11-02 21:29 X11
-rw-r--r--  1 root root        46 2007-11-02 21:30 adjtime
-rw-r--r--  1 root dv          37 2007-11-02 21:31 resolv.conf
-rw-r--r--  1 root root       278 2007-11-02 21:31 printcap
-rw-r--r--  1 root root       863 2007-11-02 21:41 mtab
dv@paris:~$ ls -ltr /etc/X11
total 144
-rw-r--r-- 1 root root    13 2006-09-12 05:44 XvMCConfig
-rw------- 1 root root   614 2007-04-15 13:50 Xwrapper.config
drwxr-xr-x 6 root root  4096 2007-04-15 13:53 fonts
drwxr-xr-x 3 root root  4096 2007-04-15 13:54 xinit
drwxr-xr-x 2 root root  4096 2007-04-15 13:59 cursors
-rw-r--r-- 1 root root    14 2007-04-15 14:01 default-display-manager
lrwxrwxrwx 1 root root    13 2007-06-21 16:33 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2007-06-22 21:38 zh_TW.Big5
drwxr-xr-x 3 root root  4096 2007-06-22 21:38 zh_CN.GB2312
drwxr-xr-x 3 root root  4096 2007-06-22 21:38 ru_RU.KOI8-R
drwxr-xr-x 3 root root  4096 2007-06-22 21:38 ko_KR.eucKR
drwxr-xr-x 3 root root  4096 2007-06-22 21:38 ja_JP.eucJP
drwxr-xr-x 3 root root  4096 2007-06-22 21:38 el_GR
drwxr-xr-x 3 root root  4096 2007-06-24 15:37 susewm
drwxr-xr-x 4 root root  4096 2007-06-24 15:37 applnk
-rw-r--r-- 1 root root   265 2007-07-04 16:55 Xsession.options
-rwxr-xr-x 1 root root  4157 2007-07-04 16:55 Xsession
-rw-r--r-- 1 root root 17371 2007-08-17 03:12 rgb.txt
drwxr-xr-x 2 root root  4096 2007-10-18 17:51 Xresources
drwxr-xr-x 2 root root  4096 2007-10-18 18:04 xkb
drwxr-xr-x 2 root root  4096 2007-10-18 18:36 xserver
drwxr-xr-x 2 root root  4096 2007-10-20 13:48 app-defaults
-rw-r--r-- 1 root root  1431 2007-10-31 14:05 xorg.conf.failsafe.bak
-rw-r--r-- 1 root root  3616 2007-10-31 14:06 xorg.conf.1
drwxr-xr-x 2 root root  4096 2007-11-01 09:07 Xsession.d
-rw-r--r-- 1 root root  2615 2007-11-02 17:44 xorg.conf~
-rw-r--r-- 1 root root  2362 2007-11-02 18:11 xorg.conf.20071102181127
-rw-r--r-- 1 root root  1417 2007-11-02 18:11 xorg.conf.failsafe
-rw-r--r-- 1 root root  2414 2007-11-02 18:12 xorg.conf.2
-rw-r--r-- 1 root root  2451 2007-11-02 18:15 xorg.conf.20071102181527
-rw-r--r-- 1 root root  1654 2007-11-02 18:18 xorg.conf.20071102181807
-rw-r--r-- 1 root root  1877 2007-11-02 21:29 xorg.conf
dv@paris:~$ date


---

### Post by bingoUV on 2007-11-03
You didn't tell me whether other users are affected. If all users are affected, do the following

Nothing except the xorg.conf seems to have changed recently. Just do
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by fearpi on 2007-11-05
Okay, I have been having this issue since, I don't know... dapper, I think. I've done a couple of clean installs since then. The sensitivity slider never does anything. I've done everything listed in this thread several times in the past couple of years. The sensitivity slider does absolutely nothing, and the sensitivity is way too low for my liking. Is it supposed to do something? Does it do anything for anybody else?

---


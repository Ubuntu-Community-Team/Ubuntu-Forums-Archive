---
title: "Problems with VNC"
date: 2018-05-19
forum: General Help
---

### Post by pocketdrummer on 2018-05-19
I've tried several different tutorials trying to get this to work, but I think I've just corrupted everything vnc related at this point.

My aim was to use a TigerVNC server on an Ubuntu 18.04 laptop and use TigerVNC client on my Windows 10 system to manage it. Initially, I was able to get connected (xfce environment), but the menu bar and dock stopped showing up, and I wasn't able to do anything that required a password (update, etc) or open the terminal.

I uninstalled all the vnc servers I could think of that I may have installed, and reinstalled it using [this tutorial]("https://help.ubuntu.com/community/VNC/Servers") for tigervnc. Unfortunately, when I try to run vncserver :1, it fails (see below). What are my options now?


```
vncserver: Failed command '/etc/X11/Xvnc-session': 256!

=================== tail -15 /home/ryan/.vnc/ryan-G73Jh:1.log ===================
syswrite() on closed filehandle WH at /usr/bin/vncserver line 888.

Xvnc TigerVNC 1.7.0 - built Dec  5 2017 09:25:01
Copyright (C) 1999-2016 TigerVNC Team and many others (see README.txt)
See http://www.tigervnc.org for information on TigerVNC.
Underlying X server release 11905000, The X.Org Foundation


Sat May 19 17:03:04 2018
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on local interface(s), port 5901
 vncext:      created VNC server for screen 0
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 175 requests (175 known processed) with 0 events remaining.
Killing Xtigervnc process ID 1905... which seems to be deadlocked. Using SIGKILL!

=================================================================================

Starting applications specified in /etc/X11/Xvnc-session has failed.
Maybe try something simple first, e.g.,
        tigervncserver -xstartup /usr/bin/xterm
ryan@ryan-G73Jh:~$
```

---

### Post by HermanAB on 2018-05-20
Windows 10 now has SSH, so VNC is obsolete.

---


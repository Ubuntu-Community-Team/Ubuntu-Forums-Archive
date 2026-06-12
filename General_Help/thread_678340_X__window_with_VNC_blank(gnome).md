---
title: "X  window with VNC blank(gnome)"
date: 2008-01-25
forum: General Help
---

### Post by pd9 on 2008-01-25
Hi, I am having a strange problem with running a vnc server from my machine. I have used both vncserver, and vnc4server from the repositories but the result is the same. I have attached an image. 

One strange thing is, the remote desktop sharing in system>administration works, but i'd like to be able to work on a different X window. I suspect there is a problem with getting gdm started, but I do not know why.

[http://img205.imageshack.us/img205/3011/vncerrordy3.jpg](http://imageshack.us)

Any ideas? I have tried connecting with many different vnc clients and the result is the same. FreeNX gives really strange errors when trying to install.

---

### Post by daflame on 2008-01-28
BTW there is a space in your image link it should be:
[http://img205.imageshack.us/img205/3011/vncerrordy3.jpg](http://img205.imageshack.us/img205/3011/vncerrordy3.jpg)

That aside, what you are seeing is just the base X server, which means no desktop environment is loaded.  There are other good forums for getting vnc4server running, but I gave up on them when I found that FreeNX which is faster and more secure is so easy to install.

Here is a forum on how to get setup:
[http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057)

---


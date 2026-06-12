---
title: "Connect to wireless display"
date: 2019-11-17
forum: General Help
---

### Post by roberthleeii on 2019-11-17
Can Ubuntu connect to a wireless display like windows and android phones? 

I frequently connect to my roku and a microsoft display adapter so this would be great if this was possible.

---

### Post by TheFu on 2019-11-18
There are software packages which can connect and mirror screens.  These are not Ubuntu specific.  They are created by project teams, just like 95% of all Linux software.

Any OS that supports X11 can display remote windows locally.  This has been part of Unix-like systems since the mid-1980s. It was designed for normal applications, not multi-media.  Do it like this:
```
$ uxterm -sb -geometry 80x25+0+0   -e ssh -X hadar &
```

For multimedia, there are better protocols that are much more efficient than trying to compress and send pixels over a network.  I use DLNA from an Ubuntu Server to android devices all-the-time.  My roku connects to the same DLNA server.
**minidlna**, **plex**, **kodi** are a mix of DLNA server, controller and renderer.  On Android, **BubbleUPnP** is all of those. They each inter-operate.  

OTOH, I know very little about Windows or Windows Phones.  Screen sending to Android has a few different tools that can be installed on Android and Ubuntu.  I've not used them because of the crap security involved. 
[https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux](https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux)
[https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)
[https://github.com/benzea/gnome-network-displays](https://github.com/benzea/gnome-network-displays) - miracast experimental implementation

Haven't looked into scrcopy before. Need to do some research.  

**update**: seems to require java.  That's a non-starter for me.  There are a few things I've learned over the decades.  Avoid hype. Trust proven tech. Never forget security and privacy just for convenience.  *New* is the enemy of stable and secure.

---


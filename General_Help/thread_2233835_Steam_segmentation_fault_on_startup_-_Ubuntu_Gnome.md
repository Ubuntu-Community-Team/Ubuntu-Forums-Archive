---
title: "Steam segmentation fault on startup - Ubuntu Gnome 14.04"
date: 2014-07-11
forum: General Help
---

### Post by muzzwood on 2014-07-11
Hi,

I've just installed Steam and it crashes after updating its files.

The terminal spits out the following:
```
/.steam/steam.sh: line 755:  4131 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
```

I've seen many threads with a similar problem but it always seems to come down to an AMD or NVIDIA driver problem.
I have an intel card and running the latest open source driver.

I was hoping someone could point me in the right direction in terms of troubleshooting.

I'm using an Asus Zenbook Prime UX31A which has Intel HD4000 video.
I'm running Ubuntu Gnome 14.04
I've tried uninstalling and reinstalling Steam of course; from both the website and from the software center.

What would be my next step? 
(pls let me know any commands needed to get extra information)

Thanks in advance!

---

### Post by dragonfly41 on 2014-07-11
When I'm trying to troubleshoot Python 2.7 segmentation faults I use the tip I found here ..

[https://bugs.launchpad.net/bzr-gtk/+bug/923824](https://bugs.launchpad.net/bzr-gtk/+bug/923824)

i.e. temporarily patch /usr/share/pyshared/gobject/constants.py

I run a simple python script to set/reset the patch.

Note that while the patch is in use other Python apps may not run. 
So after troubleshooting Steam reset constants.py to default value.

i.e.

set temporary patch in constants.py
launch Steam to pin down the source of the segmentation fault
reset constants.py to default content.

---


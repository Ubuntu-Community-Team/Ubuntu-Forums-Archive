---
title: "OS freezes entirely"
date: 2013-05-10
forum: General Help
---

### Post by Nynte on 2013-05-10
Hey,


I'm using Ubuntu 11.04 (Upgrading is not an option) both at work, as my workstation, and at home, as a media computer. In both computers, which have a completely different use cases, hardware, and software installed, suffer from what appears to be the exact same problem. They semi-randomly freeze entirely: The display freezes, mouse can't move, doesn't respond to any keyboard stroke, clock won't advance, won't respond to ping or ssh, and, if sound is playing, the last few seconds would loop. In both machines, the issue happens during a particular program is in use: in the workstation it happens when using Eclipse, and in the media machine it happens during playing a video in XBMC (It appears that it only happens with some files).

After a reboot, there's nothing in the syslog from the time of the crash.

How can I solve this issue?

Thanks

---

### Post by dino99 on 2013-05-10
that is where logs can help  :P : glance at .xsession-errors & /var/log/

but note that natty is no more maintained  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---


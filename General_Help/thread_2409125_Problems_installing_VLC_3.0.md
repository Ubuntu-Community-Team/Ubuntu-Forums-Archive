---
title: "Problems installing VLC 3.0"
date: 2018-12-28
forum: General Help
---

### Post by asb3 on 2018-12-28
I'm running ubuntu 16.04LTS, and I want to stream DVDs using chromecast.  Streming to chromecast is supported by VLC 3.0, but it is only available using snap.  I installed it, but it won't run. When I run it from the command line, I get the error:

2018/12/28 02:01:03.517285 cmd_run.go:466: WARNING: XAUTHORITY environment value is not a clean path: "/mnt/hd1/home/asb/.Xauthority"
cannot create user data directory: /home/asb/snap/vlc/768: Too many levels of symbolic links

The file 
/mnt/hd1/home/asb/.Xauthority exists

and 
/home/asb/snap/vlc/768
is created before the program crashes.

What can I do to fix the bug?

---

### Post by ajgreeny on 2018-12-28
I know little about chromecast, but I am aware that using vlc in 16.04 as a dlna client for my minidlna server fails always, whereas vlc in 18.04 works fine for that purpose; perhaps the same will be true for chromecast so an update to 18.04 may be the answer.

You can easily try it as a live system to see if that is successful.

---

### Post by asb3 on 2018-12-28
VLC 3.0 is a snap package.  I think the problem is a snap bug.

---

### Post by ajgreeny on 2018-12-28
Yes, that could be so as snaps often work quite differently to the normal apt packages, but I do not use snap packages on any of my systems so am unable to test that any further.

Try my suggestion of a live 18.04, install vlc in that and see if it will work as you want; if it does you may need to consider moving to 18.04 depending on how important that use of vlc is to you.

---


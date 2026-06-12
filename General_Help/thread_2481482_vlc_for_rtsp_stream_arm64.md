---
title: "vlc for rtsp stream arm64"
date: 2022-11-30
forum: General Help
---

### Post by thephantom1972 on 2022-11-30
Hi,  

I bought an ODROID C4 today. It is installed with Ubuntu linux LTS. I  did an update to the desktop version via sudo apt-get install  ubuntu-desktop. Fully updated and that gives me version 22.04 LTS, 64  bits, Gnome 42.5 with X11.

  The intention is that a number of security streams will streamed with  rtsp protocol from unifi. So I want to install vlc media player.  However, I don't have Ubuntu Software Center. So i tried to installed it  via "sudo snap install vlc". However, I get the error message:  error:  snap "vlc" is not available on stable for this architecture (arm64) but          exists on other architectures (amd64).  

Via "apt://vlc" I did get VLC installed, but the rtsp stream doesn't  work with that. Is there an way to get this work with the snap version.  It seems that the snap version can use rtsp. 

ps the streaming is done by magicmirror2.

---

### Post by MAFoElffen on 2022-11-30
Current Version of VLC is 3.0.18

Current version of VLC in 22.04 in APT is 3.0.16-1build7

Current Version of VLC in 23.04 in APT is 3.0.17.4-5

I do not know which versions are available in Snap. It sounds like it is not available for Arm at all right? Isn't that what you said?

Which version are you wanting? (By version Number.)

---


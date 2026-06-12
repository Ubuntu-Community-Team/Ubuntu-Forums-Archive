---
title: "deluged causes a system error in Ubuntu when run as a service"
date: 2019-03-01
forum: General Help
---

### Post by dalekky on 2019-03-01
deluged is causing a system error in Ubuntu 18.04 (and 16.04) when started as a systemd service at startup.

I know this is the cause of the system error because my Ubuntu 16.04 system started giving the system error shortly after I installed deluged as a service, then after formatting the drive and making a fresh install of Ubuntu 18.04 all the problems went away, then the problem started again the moment I installed deluged as a service again.

Also, I don't understand why, but having the deluged daemon installed as a service also causes an audio surge to be sent through the speakers at startup and shutdown of the computer. This is another problem which came back the instant deluged was installed as a service. At first I thought the audio surge was just a normal feature of the hardware, but then it went away after the fresh install of Ubuntu 18.04 and started happening again only after installing the deluged service.

Anyone want to try solve this mystery?

Hardware is an Apple Macmini (model identifier macmini2,1)
OS is Ubuntu 18.04.2
deluged and deluge-web installed from deluge-team ppa and installed as systemd service using the guide at [https://dev.deluge-torrent.org/wiki/UserGuide/Service/systemd](https://dev.deluge-torrent.org/wiki/UserGuide/Service/systemd)

view my dmesg output here - [http://paste.ubuntu.com/p/9Wb5BXrsDh/](http://paste.ubuntu.com/p/9Wb5BXrsDh/)

---


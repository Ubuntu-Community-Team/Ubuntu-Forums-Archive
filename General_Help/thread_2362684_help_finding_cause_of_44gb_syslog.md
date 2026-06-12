---
title: "help finding cause of 44gb syslog"
date: 2017-05-31
forum: General Help
---

### Post by cbc02009 on 2017-05-31
I have an ubuntu system that I use as a NAS and plex server. I use TigerVNC to control the server from my desktop PC. I was working on it this morning when i got an error that the hard drive was full, and it was pretty much all taken up by one file: syslog. The file contains 44gb of messages such as the ones below, but I don't know what they mean. Can anyone help me figure out what it is that's causing this?

```
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      ec2-34-209-20-162.us-west-2.compute.amazonaws.com
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.241
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.243
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.244
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      delta.ip-colo.net
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.10
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.242
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      delta.ip-colo.net
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      91.195.103.155
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.11
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      31.44.191.110
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      31.44.191.107
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.8
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      delta.ip-colo.net
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.9
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.241
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.243
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.244
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.12
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      delta.ip-colo.net
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.7
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.13
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      delta.ip-colo.net
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      139.60.160.242
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      134.213.222.59
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      delta.ip-colo.net
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      91.195.103.155
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      31.44.191.107
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      31.44.191.110
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      77.72.82.10
May 31 12:41:39 Sakura vino-server.desktop[3348]: 31/05/2017 12:41:39 PM      unknown.static.123.net
```

---

### Post by gsahli on 2017-05-31
Turn off the VNC server and see if entries continue.
vino is the standard VNC server, not Tight/TigerVNC. Did you set that up previously?
It looks like you are being hammered by an IP-spoofing client. (ie, someone is trying to break into your server.)

---

### Post by cbc02009 on 2017-06-01
Thanks, that's kind of what I figured, but I wanted to make sure. I wasn't aware that VNC was outward facing. Is there a way to only allow local computers to remote control the server?

---

### Post by gsahli on 2017-06-01
Does that server have a world-reachable IP address? (mostly other than 10.x, 172.x, 192.168.x)
In general, a router can be configured to block specified ports. For us home router users, VNC isn't normally world-reachable.

---


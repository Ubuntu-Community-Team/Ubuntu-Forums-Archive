---
title: "Setting up VNCServer on Ubuntu Edgy"
date: 2007-04-10
forum: General Help
---

### Post by gavinjb on 2007-04-10
Hi,

I am trying to configure VNCServer to run on my machine, but all I get is either:

```
vncviewer: read: Connection reset by peer
```

or

```
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

I have tried running  sudo netstat -tap | grep xinetd and it looks like it is running
```
tcp        0      0 *:5901                  *:*                     LISTEN     4828/xinetd 
```

I tried setting this up from thread ([http://ubuntuforums.org/showthread.php?t=259448)](http://ubuntuforums.org/showthread.php?t=259448)), does anyone have any ideas what I have done wrong.

Thanks,


Gavin,

---

### Post by bmt on 2007-04-13
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=197964").  There's a bug in the Edgy vnc4server, if that's what you're using.

---


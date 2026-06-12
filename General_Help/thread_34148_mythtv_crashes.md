---
title: "mythtv crashes"
date: 2005-05-13
forum: General Help
---

### Post by mdbarton on 2005-05-13
I'm having trouble running mythtv.  I run mythtv-setup - everything looks ok, but when I run the front end and go to Watch television, I just get a black screen, then it crashes.  This is the output:

```
mythtv@bluemax:~$ /etc/init.d/mythtv-backend start
Starting MythTV server: mythbackend/usr/bin/mythbackend already running.
mythtv@bluemax:~$ mythfrontend &
[1] 8388
mythtv@bluemax:~$ 2005-05-13 19:45:27.172 mythfrontend version: 0.17.20050130-1 www.mythtv.org
2005-05-13 19:45:27.173 Enabled verbose msgs : important general
2005-05-13 19:45:27.539 Switching to square mode (G.A.N.T.)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2005-05-13 19:45:28.508 Joystick disabled.
2005-05-13 19:45:28.595 Registering Internal as a media playback plugin.
2005-05-13 19:45:37.886 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2005-05-13 19:45:37.993 Using protocol version 14
2005-05-13 19:45:38.118 Using protocol version 14
Errm, event socket just closed.
2005-05-13 19:45:58.126 ReadStringList timeout (quick).
Remote encoder not responding.
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
Could not connect to server
Could not connect to server
2005-05-13 19:45:58.136 WriteStringList: Bad socket
2005-05-13 19:45:58.136 ReadStringList: Bad socket
Remote encoder not responding.
2005-05-13 19:45:58.206 Disable DPMS
2005-05-13 19:45:58.267 WriteStringList: Bad socket
2005-05-13 19:45:58.268 ReadStringList: Bad socket
Remote encoder not responding.
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)
ASSERT: "i <= nodes" in /usr/include/qt3/qvaluelist.h (372)

[1]+  Segmentation fault      mythfrontend
``` 

Can anyone point out where I might be going wrong?

---

### Post by mdbarton on 2005-05-15
Ok, now got it working.  Added my main user id to the mythtv group so I can run mythtv whilst logged on as me (ratherthan logging in as mythtv).  I still get the crash, but if I run
```
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
sudo /etc/init.d/mythtv-backend stop
sudo /etc/init.d/mythtv-backend start
```Then everything works ok.
How do I make sure these are running when I boot up / log in?
The next problem is I cannot hear any sound.  Anybody got this working with a Hauppauge WinTV PCI and a soundblaster live (output of tv card is fed into the line-in on the soundcard).  I get sound no problem with TV time.

---


---
title: "Trying to get x2go to work with xfce/xubuntu"
date: 2016-11-23
forum: General Help
---

### Post by vincent36 on 2016-11-23
I cannot figure out why, but on a clean Xubuntu 16.10 install (both sides) i cannot get a xfce desktop from the server. I get the connection and immediately i get a disconnect as well.

```
 Connection timeout, aborting
 NXPROXY - Version 3.5.0
 

 Copyright (C) 2001, 2010 NoMachine.
 See http://www.nomachine.com/ for more information.
 

 Info: Proxy running in client mode with pid '19404'.
 Session: Starting session at 'Wed Nov 23 11:15:08 2016'.
 Info: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.
 Info: Connecting to remote host 'localhost:41316'.
 Info: Connection to remote proxy 'localhost:41316' established.
 Info: Connection with remote proxy completed.
 Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
 Info: Using LAN link parameters 1536/24/1/0.
 Info: Using pack method 'adaptive-9' with session 'unix-kde-depth_24'.
 Info: Not using NX delta compression.
 Info: Not using ZLIB data compression.
 Info: Not using ZLIB stream compression.
 Info: Not using a persistent cache.
 Info: Forwarding X11 connections to display ':0.0'.
 Session: Session started at 'Wed Nov 23 11:15:08 2016'.
 Info: Established X server connection.
 Info: Using shared memory parameters 0/0K.
 Session: Terminating session at 'Wed Nov 23 11:15:10 2016'.
 Session: Session terminated at 'Wed Nov 23 11:15:10 2016'.
 
```

What am i doing wrong?

---

### Post by TheFu on 2016-11-24
x2go client is tied to x2go server. Don't use nomachine stuff.

Step 1 is to setup ssh so the client can talk to the server. Do that first. 

Then follow the instructions for x2go on their website. Be certain to use their PPA for both the client AND the server machines. 

If there are issues, look a the log files. The client has logs and the server has logs. The log files will say what you didn't setup.

---


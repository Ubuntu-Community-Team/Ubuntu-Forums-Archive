---
title: "NXServer error message"
date: 2013-01-27
forum: General Help
---

### Post by shutterbc on 2013-01-27
****UPDATE** Upgrading to nxserver free edition 3.5.0-11 seems to be working better, perhaps it was a bug in version 3.2.**

Hi, I'm trying to figure out the cause of a particular error and wondering if anyone else has seen this before.

**Prior events**:
I can establish a working NX session in 12.10 running nxserver 3.2.0-7 and unity works great in 2D mode.  I'm using NX client 4.0.181 preview 6 to connect.
I then disconnect from the session (without terminating it).

When I later try to connect to this session, I receive the following error:

```
14028 13112 16:33:06 106.787 Connection: Read from FD#1292 failed with error 149: 'Connection reset by peer'.
14028 13112 16:33:06 107.787 Connection: Waiting for I/O error on the output socket.
14028 13112 16:33:06 107.787 Connection: Read from FD#1156 failed with error 149: 'Connection reset by peer'.
14028 13112 16:33:06 107.787 Connection: Connection at 0x55279b8 failed.
14028 13112 16:33:06 107.787 ClientSession: Runnable at 0x55279b8 caused the session at 0x34770f0 to fail.
14028 13112 16:33:06 107.787 ClientSession: Failing reason is 'The session negotiation failed.

Error: No running session with id '03D3DD9C809E0AF632C3CFBFE1A0B52A''.
```


Not sure why I'm getting this since I know that the session is still running, as shown here:

```
NX> 127 Session list:

Display Username                         Remote IP       Session ID                       Node
------- -------------------------------- --------------- -------------------------------- -----------
1066    rich                             -               03D3DD9C809E0AF632C3CFBFE1A0B52A localhost:22

NX> 999 Bye.
```

Any recommendations on what's next in the troubleshooting process?

---

### Post by shutterbc on 2013-01-27
Interestingly, if I create a new session and then terminate it, I can log into the old session properly.

Anyone else experiencing this?

---

### Post by shutterbc on 2013-02-05
See above; issue appears to be solved after upgrading nxserver to 3.5.0.

---


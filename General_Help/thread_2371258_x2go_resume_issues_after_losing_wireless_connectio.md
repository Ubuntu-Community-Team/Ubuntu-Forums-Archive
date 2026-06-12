---
title: "x2go resume issues after losing wireless connection"
date: 2017-09-12
forum: General Help
---

### Post by c_xy on 2017-09-12
Hello,


We use x2go to connect to a server from various windows and mac clients.

There server is a dell r730 with Ubuntu 14.04 LTS installed. We are using Mate as the DE.

The problem we run into is when we are connected on laptop (mac or windows) and we lose a wireless connection on the laptop. When we try to resume the session, the previous existing session pops up for about 1 second then it immediately suspends the session.

Here is the out from the session.log file


Here is the code when we start the session from the mac client. The red font is when we lose connection to the server due to wireless or the laptop hibernating.

```

Info: Agent running with pid '357943'.
Session: Starting session at 'Sat Sep  9 16:01:46 2017'.
Info: Proxy running in server mode with pid '357943'.
Info: Waiting for connection from 'localhost' on port '45259'.
Info: Accepted connection from '127.0.0.1'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using agent parameters 5000/0/50/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Listening to X11 connections on display ':50'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/0/0K.
Info: Using alpha channel in render extension.
Info: Using local device configuration changes.
keyboard file created
Session: Session started at 'Sat Sep  9 16:01:56 2017'.
Info: Screen [0] resized to geometry [1440x878] fullscreen [1].
Warning: No data received from remote proxy within 34 seconds.
[COLOR=#ff0000]Session: Display failure detected at 'Sat Sep  9 16:16:17 2017'.[/COLOR]
[COLOR=#ff0000]Session: Suspending session at 'Sat Sep  9 16:16:17 2017'.[/COLOR]
[COLOR=#ff0000]Error: Connection with remote peer broken.[/COLOR]
[COLOR=#ff0000]Error: Please check the state of your network and retry.[/COLOR]
[COLOR=#ff0000]Session: Session suspended at 'Sat Sep  9 16:16:19 2017'.[/COLOR]



```

When we try to resume a session, here is the log info:

```

Session: Resuming session at 'Tue Sep 12 13:42:40 2017'.
Info: Proxy running in server mode with pid '357943'.
Info: Waiting for connection from 'localhost' on port '45259'.
Info: Accepted connection from '127.0.0.1'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using agent parameters 5000/0/50/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Listening to X11 connections on display ':50'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/0/0K.
Info: Not using local device configuration changes.
nxagentReconnectFailedFonts: WARNING! Font server tunneling not retrieved.
nxagentReconnect: WARNING! Unable to retrieve all the fonts currently in use. Missing fonts have been replaced.
keyboard file created
Session: Session resumed at 'Tue Sep 12 13:42:42 2017'.
Session: Suspending session at 'Tue Sep 12 13:42:42 2017'.
Info: Waiting the cleanup timeout to complete.
Session: Session suspended at 'Tue Sep 12 13:42:43 2017'.




```

Any help would greatly be appreciated.   

c

---

### Post by TheFu on 2017-09-14
Is the ssh keepalive setting working?  Set that in your ~/.ssh/config file.

---


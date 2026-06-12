---
title: "FreeNX Dapper connection problem."
date: 2006-09-10
forum: General Help
---

### Post by JeBeKe on 2006-09-10
After a successful authentication, waiting for the negotiation between client en server, I get kicked out. The log file gives the following info:

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

NXAGENT - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '11211'.
nxagentProcessOptionsFile: Option file is [/home/jan/.nx/C-LinuxServer-1000-F305ED495AEA8AAADB245F79C6CD79F2/options].
nxagentProcessOptionsFile: Option file is 187 bytes long.
nxagentParseOptionString: Warning ignored option 'cache' = '8M'.
nxagentParseOptionString: Warning ignored option 'images' = '32M'.
nxagentParseOptionString: Warning ignored option 'link' = 'adsl'.
nxagentParseOptionString: Warning ignored option 'type' = 'unix-gnome'.
nxagentParseOptionString: Warning ignored option 'cleanup' = '0'.
nxagentParseOptionString: Warning ignored option 'accept' = '127.0.0.1'.
nxagentParseOptionString: Warning ignored option 'cookie' = 'c9cacd8617e99c6c3d398eeb6ea2e03b'.
nxagentParseOptionString: Warning ignored option 'samba' = '0'.
nxagentParseOptionString: Warning ignored option 'media' = '0'.
Info: Proxy running in server mode with pid '11211'.
Info: Waiting for connection from '127.0.0.1' on port '5000'.
Info: Accepted connection from '127.0.0.1' on port '45247'.
Info: Connection with remote proxy established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using split parameters 100/16384/6144/1024KB.
Info: Using adsl link parameters 8192/8/10/50.
Info: Using agent parameters 49152/0/0.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: Not using processor load limit.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X client connection.
Info: Using shared memory support in X server.
Info: Using fast copy area mode in agent.
Info: Using fast get image mode in agent.
Info: Using render cleanup parameters 8/20/23/24/25/26.
Info: Using image cleanup parameters 0/0/0/0.
Info: Detected window manager.
Info: Not using local device configuration changes.
Info: Using alpha channel in render extension.
error opening security policy file /etc/X11/xserver/SecurityPolicy
Info: Adding the X connection 3 to the device set.
Unable to initialize XKEYBOARD extension.
Could not init font path element /usr/share/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Info: Session started, state is [SESSION_UP].
Info: Entering dispatch loop with exception 0x0.
AUDIT: Sun Sep 10 16:13:37 2006: 11211 nxagent: client 1 rejected from local host
Xlib: connection to "unix:1000.0" refused by server
Xlib: No protocol specified


(gnome-session:11214): Gtk-WARNING **: cannot open display:  
Info: Exiting dispatch loop with exception 0x2.
Info: End of session requested by agent termination.
Info: Waiting for a further signal to complete.
Info: Shutting down the link and exiting.
Warning: Parent process appears to be dead. Exiting keeper.

Anyone any idea?

---


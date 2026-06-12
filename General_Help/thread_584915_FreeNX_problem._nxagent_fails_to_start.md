---
title: "FreeNX problem. nxagent fails to start"
date: 2007-10-21
forum: General Help
---

### Post by MegaSvensk on 2007-10-21
Hi,

I'm trying to get FreeNX working on my Ubuntu 7.10 so that I can access my desktop and files from work and other places. I did try VNC but it lacked a vital feature, namely audio.

I can't seem to get the FreeNX working though. When I attempt to connect (with NX Client on Windows), I am connected and I pass the authentication but then I get a "Session startup failed" error.

This is the log file:
```
NX> 203 NXSSH running with pid: 3968

NX> 285 Enabling check on switch command

NX> 285 Enabling skip of SSH config files

NX> 285 Setting the preferred NX options

NX> 200 Connected to address: 192.168.1.51 on port: *****

NX> 202 Authenticating user: nx

NX> 208 Using auth method: publickey

HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)

NX> 105 hello NXCLIENT - Version 1.4.0

NX> 134 Accepted protocol: 1.4.0

NX> 105 SET SHELL_MODE SHELL

NX> 105 SET AUTH_MODE PASSWORD

NX> 105 login

NX> 101 User: vandelay

NX> 102 Password: 

NX> 103 Welcome to: vandelay-desktop user: vandelay

NX> 105 listsession --user="vandelay" --status="suspended,running" --geometry="1152x864x32+render+fullscreen" --type="unix-gnome"

NX> 127 Sessions list of user 'vandelay' for reconnect:



Display Type             Session ID                       Options  Depth Screen         Status      Session Name

------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------





NX> 148 Server capacity: not reached for user: vandelay

NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --samba="1" --media="1" --mediahelper="esd" --session="testing" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/se" --screeninfo="1152x864x32+render+fullscreen" 



NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)

NX> 700 Session id: vandelay-desktop-1000-27029F78C5E4F767D63D3C1C8C720928

NX> 705 Session display: 1000

NX> 703 Session type: unix-gnome

NX> 701 Proxy cookie: a2d4ad3e3d92389e6537000b474ce36b

NX> 702 Proxy IP: 127.0.0.1

NX> 706 Agent cookie: a5406737c564723ad4ef302796bdbea0

NX> 704 Session cache: unix-gnome

NX> 707 SSL tunneling: 1

NX> 105 /usr/lib/nx/nxserver: line 880: 22194 Avslutad                ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )

NX> 504 Session startup failed.

NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1

NX> 1001 Bye.

NX> 280 Exiting on signal: 15
```

I am guessing I have to change that unrecognized option but I have no idea where and to what.

Does anyone know how to get this working?

Thanks.

---

### Post by daflame on 2007-11-22
Update to the latest FreeNX 0.7.1
Click [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to see the post.  Please contribute to the refinement of the installation.

---


---
title: "FreeNX problem. Connection fails with error &quot;Session startup failed&quot;"
date: 2007-10-18
forum: General Help
---

### Post by MegaSvensk on 2007-10-18
Hi,

I'm trying to connect to my Ubuntu 7.04 with FreeNX (I don't want to use VNC because it lacks sound support) and I can't get it to connect. When I try to connect, I get the error message: "Session startup failed."

Here's the log:
```
NX> 203 NXSSH running with pid: 1372

NX> 285 Enabling check on switch command

NX> 285 Enabling skip of SSH config files

NX> 285 Setting the preferred NX options

NX> 200 Connected to address: 192.168.1.51 on port: 58211

NX> 202 Authenticating user: nx

NX> 208 Using auth method: publickey

HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)

NX> 105 hello NXCLIENT - Version 1.4.0

NX> 134 Accepted protocol: 1.4.0

NX> 105 SET SHELL_MODE SHELL

NX> 105 SET AUTH_MODE PASSWORD

NX> 105 login

NX> 101 User: ********

NX> 102 Password: 

NX> 103 Welcome to: ******** user: ********

NX> 105 listsession --user="********" --status="suspended,running" --geometry="1152x864x32+render+fullscreen" --type="unix-gnome"

NX> 127 Sessions list of user '********' for reconnect:



Display Type             Session ID                       Options  Depth Screen         Status      Session Name

------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------





NX> 148 Server capacity: not reached for user: ********

NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --samba="1" --media="1" --mediahelper="esd" --session="testing" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/se" --screeninfo="1152x864x32+render+fullscreen" 



NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)

NX> 700 Session id: ********-1000-3D2BD8439E3C4B1B9CE71C007A627B58

NX> 705 Session display: 1000

NX> 703 Session type: unix-gnome

NX> 701 Proxy cookie: 0b8089ece13421e91211df683f8b71af

NX> 702 Proxy IP: 127.0.0.1

NX> 706 Agent cookie: a5406737c564723ad4ef302796bdbea0

NX> 704 Session cache: unix-gnome

NX> 707 SSL tunneling: 1

NX> 504 Session startup failed.

NX> 280 Exiting on signal: 15
```

I tried to connect once before this and then I got a different error that said something like "nxagent failed to start with: Unrecognized option: 1".

Does anyone know how to get this working?

---

### Post by daflame on 2007-11-22
If you update it might solve your problem

Click [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to see the post.  Please contribute to the refinement of the installation.

---


---
title: "FreeNX Help"
date: 2007-04-01
forum: General Help
---

### Post by RockyRock on 2007-04-01
Hi, I just switched from windows xp to ubuntu.  I tried to install FreeNX as a package by adding a repository. 

But when I access the linux machine from other clients (a windows xp system). I got the following messages:

NX> 203 NXSSH running with pid: 724
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 1********* on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: lei
NX> 102 Password: 
NX> 103 Welcome to: lei-desktop user: lei
NX> 105 listsession --user="lei" --status="suspended,running" --geometry="1024x768x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'lei' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: lei
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="0" --encryption="1" --cache="8M" --images="32M" --media="0" --session="Lab" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/en_US" --screeninfo="1024x740x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: lei-desktop-1000-0787EDDC23D4CBEBC8B84CAFA6EC0802
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 3a26b417659be4dadf245457b6650ab7
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 688f227b9cad4edeed15f067e04d3764
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 891: 25292 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.

Any help? is this the problem with the server?

Thanks a lot!

Really frustrated with linux...

---

### Post by magean on 2007-04-03
This problem is widespread. If you are using the 2.?? version of nomacines client? 
Try [http://www.industrial-statistics.com/nxclients/nxclient-1.5.0-114.exe](http://www.industrial-statistics.com/nxclients/nxclient-1.5.0-114.exe) this is an old version of the client which works with freeNX.

If no more than 2 named users will log on to the server I would skip nxfree altogether and use nomachines free version.


Download client node and free server from nomachine.com

wget [http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-17_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-17_i386.deb)
wget [http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-22_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-22_i386.deb)
wget [http://64.34.161.181/download/2.1.0/Linux/FE/nxserver_2.1.0-22_i386.deb](http://64.34.161.181/download/2.1.0/Linux/FE/nxserver_2.1.0-22_i386.deb)

sudo apt-get install libstdc++2.10-glibc2.2 
(required by nxclient try without and dpkg will tell you what dependencies are missing)

sudo dpkg -i nxclient*

sudo dpkg -i nxnode*

sudo dpkg -i nxserver*

---

### Post by RockyRock on 2007-04-04
Thanks! I installed a freenx-1.5.0-103.exe from
[http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768](http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768)
and it works perfect now.

Seems other versions still have some problem. Only this version works on my machine.

Thanks!!

---

### Post by magean on 2007-04-04
If you use freenx 0.6 you can use the latest NX client. 
[http://opensource.dental-on-line.com/?page_id=23](http://opensource.dental-on-line.com/?page_id=23)

Make sure you uninstall everything connected to freenx 0.4 before you install 0.6 to make sure everything works.

---


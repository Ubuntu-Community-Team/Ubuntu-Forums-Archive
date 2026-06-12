---
title: "FreeNX stopped working on Gutsy"
date: 2008-05-14
forum: General Help
---

### Post by sola on 2008-05-14
I have no idea why but my perfectly working FreeNX installation stopped working today. It is probably due to some security update because I haven't installed anything recently by myself.

The FreeNX server is on a relatively fresh Gutsy machine. I have the following more important packages on it:
- freenx 0.7.1-1
- nxagent 3.1.0-0
- nxlibs 3.1.0-0

The client machine is also a Gutsy installation with only the NX client installed on it.

The NX connection log:
---------------------------------------------
NX> 203 NXSSH running with pid: 8449
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.151 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: sola
NX> 102 Password: 
NX> 103 Welcome to: mythbuntu user: sola
NX> 105 listsession --user="sola" --status="suspended,running" --geometry="1680x1050x24+render+fullscreen" --type="unix-gnome"
NX> 127 Sessions list of user 'sola' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: sola
NX> 105 startsession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Mythbuntu-2" --type="unix-gnome" --geometry="1680x1044" --fullscreen="1" --client="linux" --keyboard="pc105/hu" --screeninfo="1680x1050x24+render+fullscreen" 

Permission denied (publickey,password).
NX> 280 Exiting on signal: 15
--------------------------------------------------------------


I installed the system using [daflame]("http://ubuntuforums.org/member.php?u=256480")'s instructions on this thread: [http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057) ([B]      Installing FreeNX in Ubuntu 7.10 Gutsy)

[/B]Any help is appreciated!

---

### Post by iswa on 2008-05-14
This could be related to the recent ssh-vulnerability and patch - you may have to regenerate your keys and re-swap them with the server.

A couple of links related to this:
[http://mail.kde.org/pipermail/freenx-knx/2005-August/001869.html](http://mail.kde.org/pipermail/freenx-knx/2005-August/001869.html)
[http://ubuntuforums.org/archive/index.php/t-29013.html](http://ubuntuforums.org/archive/index.php/t-29013.html)

Here's the link to the original advisory:
[http://www.ubuntu.com/usn/usn-612-4](http://www.ubuntu.com/usn/usn-612-4)

HopeThisHelps.

---

### Post by sola on 2008-05-15
Thanks for helping.

I gave up fighting yesterday (putting it back into operation was urgent) and reinstalled the server machine (to Hardy).
The fresh install seems to work well with the Gutsy client.

---

### Post by daflame on 2008-08-03
> **sola said:**
> Thanks for helping.

I gave up fighting yesterday (putting it back into operation was urgent) and reinstalled the server machine (to Hardy).
The fresh install seems to work well with the Gutsy client.

I know this is ancient, but there are updates for FreeNX for NX 3.2.0 now.

---


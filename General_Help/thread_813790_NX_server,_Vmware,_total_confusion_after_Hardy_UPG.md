---
title: "NX server, Vmware, total confusion after Hardy UPG"
date: 2008-05-31
forum: General Help
---

### Post by drifting on 2008-05-31
I had a perfect working server, 64 bit AMD Ubuntu. In a reckless moment I decided to upgrade to Hardy. For the life of me I cannot get NX working, here is the error I get, and this is after removing existing packages and reinstalling with all the latest, so any help with this welcome. The irritating part is that I have the same problem with VMware server, complete reinstall and configure and all it does is pretend to start up then just vanish, so with a combination of NX and vmware I am doing a lot of dashing back and forward to the roof space in my house (where the server is hiding)

NX> 203 NXSSH running with pid: 6836
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.0.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: paul
NX> 102 Password: ********
NX> 103 Welcome to: vs user: paul
NX> 105 Listsession --user="paul" --status="suspended\054running" --geometry="2560x1024x24+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: paul
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="10.0.0.1" --type="unix-gnome" --geometry="2560x993" --client="linux" --keyboard="pc105\057gb" --screeninfo="2560x993x24+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: A5B7DD0F. To get detailed information about
NX> 595 ERROR: the error search for the string A5B7DD0F in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

Regards Paul

---

### Post by drifting on 2008-06-04
Bump 


Anyone got a clue ?

---

### Post by thecrane on 2008-06-22
Hey drifting,

Did you get any further with this?  I seem to be having the same problem.  :(

---

### Post by drifting on 2008-06-23
Yes and no, Yes I resolved the problem with VMware by yet another remove and followed the thread and rather good script someone wrote for installing VMware which I found in the forum.

As for NX server, I have just given up! It was more hassle than it was worth and I went back to using VNC. Would have preferred to use it, but no one had any idea, and googling bought up nothing as well. The NX support site was about as useless as a chocolate teapot.

Regards Paul.

---

### Post by feld on 2008-08-21
I'm having this issue right now, too, except without any VMWare. Anyone have a clue?

---


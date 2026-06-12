---
title: "VNC fails to start"
date: 2023-08-13
forum: General Help
---

### Post by tayvee on 2023-08-13
Hi, I've completed a new clean install Ubuntu 22.04.3 LTS, selecting the minimum software version during install process. I have pi-hole up and running, and I'm not trying to get VNC server up.

Starting with RVNC from here [https://www.realvnc.com/en/connect/download/viewer/linux/](https://www.realvnc.com/en/connect/download/viewer/linux/) the install process seems to work okay, however when I run the application is says "Authentication Required. Authentication is needed to run '/etc/vnc/vncservice' as super user'. That's fine, I input the password, and then quite literally nothing happens.

After several attempts I've tried NoMachine from the Ubuntu Software store. It again installs okay, however when I run the software, again nothing happens. The application doesn't start, no process are shown in the activity monitor, it's as if I didn't even click on it.

Any ideas?

Any help would be gratefully received.
Thanks

---

### Post by TheFu on 2023-08-13
vncserver shouldn't be run as root.  Ubuntu doesn't use root for stuff like that.

NoMachine is proprietary and uses the NX protocol, not VNC.  A F/LOSS alternative is x2go. There's a client and a server.  Setup ssh first between the client and server.  Really, when connecting between systems on the same LAN, just use ssh. No full desktop is needed.  A pihole doesn't have any GUI, so only the web interface will be used 95% of the time.  The rest of the  time, an ssh connection (text only) will be used to patch and maintain the pi-hole.  No GUI.

I use both pi-hole and x2go myself.  x2go is only used when I'm traveling and connecting back to my home network. It is just too much overhead to use for normal GUI programs on the same LAN. For those, I use **ssh -X** to tunnel X11 through ssh. Much easier, faster, and lets the remote programs fully integrate with my local workstation programs.

VNC security is too poor to use without setting up an ssh tunnel (or full VPN) anyway, so why not use a more efficient, secure, protocol like NX?

If it were me, I'd purge VNC and NoMachine stuff completely, setup ssh, then add x2go on both sides only if access over the internet is needed. It sorta just works.

---

### Post by HermanAB on 2023-08-13
Note that VNC is mostly a Windows thing and it has all the insecurities one would expect from Windows ME.  Unix//Linux systems work better with SSH and it can do everything VNC does plus much more.

Nowadays even Windows 11 ships with a limited version of SSH.

---

### Post by tayvee on 2023-08-13
Thanks both, but no ideas on why RVNC wouldn't start?
I'll give ssh -X a try.
Cheers

---


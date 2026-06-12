---
title: "Assistance Needed with Setting Up Secure Remote Desktop on Raspberry Pi 5 with Ubuntu"
date: 2024-02-21
forum: General Help
---

### Post by torsten-123 on 2024-02-21
Hello Ubuntu Community,


I'm new to Linux and have been attempting to set up a remote desktop environment on my Raspberry Pi 5 running Ubuntu Desktop 23.10. Despite my efforts, I've encountered some challenges that I haven't been able to overcome on my own. I'm reaching out for guidance or suggestions from the community.


_What I've Tried:_


VNC Server Installation: I've installed x11vnc as my VNC server on the Raspberry Pi to enable remote desktop access.
SSH Service: I've ensured that the SSH service is active and enabled on boot to secure the connection.
SSH Tunneling: Attempted to create an SSH tunnel for VNC with the command: ssh -L 5900:localhost:5900 pi@<Raspberry_Pi_IP_Address> -N to secure the VNC connection.
Firewall Configuration: I've adjusted the UFW firewall settings to allow SSH connections.
VNC Connection Attempts: Using VNC Viewer, I tried connecting to localhost:5900 through the established SSH tunnel, but encountered errors like "getpeername: Invalid argument (22)" and "The port on which the computer is listening for a connection could not be contacted."


_My Setup:_


Device: Raspberry Pi 5
OS: Ubuntu Desktop 23.10


_Objective:_


I'm aiming for a secure remote desktop setup that allows me to connect to the Ubuntu Desktop environment from the login screen. Given my newness to Linux and the specific challenges I've faced, I would greatly appreciate any advice on how to achieve a secure and functional remote desktop setup on this platform. A secure remote desktop solution is preferred for enhanced security and privacy.


Thank you in advance for your time and assistance. Any suggestions, tutorials, or guidance would be incredibly helpful as I navigate this setup.



Best regards,
Torsten

---

### Post by TheFu on 2024-02-21
a) get ssh working first. Use ssh-keys or ssh-certs for authentication, never passwords.
b) Use a light DE - NOT Gnome or KDE.  LXQt, XFCE, Mate are better choices
c) Use x2go - this uses ssh for network encryption and authentication onto the machine.  ssh is part of the NX protocol. X2go clients exist for Linux, MacOS and that other OS.

VNC is not secure.  There are some complications because it assumes you understand how X/Windows works. If you don't, then it is hard to setup a working configuration.
RDP is not secure.

For x2go how-to, [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

I've never tried x2go to/from a Raspberry PI, so after you setup the repo, be certain that the packages will load. It appears that Pi hardware has been supported since 2021. I just did a quick search.

BTW, please realize that 23.10 support ends in June '24, so when 24.04 is released, you'll have a few months to upgrade.  24.04 is an LTS, so it will have 3 yrs of support for those desktops.  GUIs really add overhead to any computer, so they aren't a good idea.  You'd be better off learning to use ssh/CLI only on a raspberry pi.

Here's a good book (free, no hassle download) on using the shell on Linux systems: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)
Linux knowledge and skills build on prior knowledge and skills.  It is nearly impossible to jump into intermediate level stuff without having the basics down first.  Setting up ssh is a little more than beginner knowledge.  Setting up a remote desktop with x2go isn't much harder, but the concepts are often new, so people struggle.

I've used x2go from 5 continents to remote back to my home systems. However, for my raspberry pi systems, I always just use ssh.

x2go feels 2-3x faster than either VNC or RDP.  With proper tuning, I've used an ISDN connection from very remote, satellite-only, links to get a desktop back home.  The tricks are to use higher compression modes, tell the x2go session that your bandwidth is at least 1 less than the true bandwidth, and don't setup file sharing, printing or audio through the NX connection.

If you get stuck, there must be 50 youtube videos on setting up x2go.

---

### Post by torsten-123 on 2024-02-21
Thanks for the info! I will give x2go a try. I am using 23.10 because 22.04.3 LTS is not supported on the pi 5.

---

### Post by TheFu on 2024-02-22
> **torsten-123 said:**
> Thanks for the info! I will give x2go a try. I am using 23.10 because 22.04.3 LTS is not supported on the pi 5.

Yep. I have Pi 2, 3, 4, and 5 computers here.  My Pi 5 is waiting for some specific software to be ported.  I'm using that software on a Pi4 today and it works fantastic, though I wish the fan on the Pi4 were quiet.  Thermal management on the v5 should be quieter.  At least I hope it is.

BTW, be certain to take advantage of the power that a Pi5 has and run some containers on it.  It is like having multiple machines, but with 10x less overhead than what a normal virtual machine would require.  Plus if you keep the GUI off it and used wired GigE ethernet connections, then you should be able to run a number of home servers - like nextcloud, wallabag, pi-hole on the same physical system.

---


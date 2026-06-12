---
title: "pptp setup help"
date: 2005-04-12
forum: General Help
---

### Post by halo five on 2005-04-12
Hi, I'm a Linux half-noob, trying out ubuntu 5.04 as a Windows replacement at home.  So far I'm very impressed!  Installation was a dream, Gnome 2.10 is slick, and the apt gui is a dream come true!

However, I could use help setting up pptp.  My work uses a pptp vpn with no MPPE.  I understand there is no GUI to configure pptp in ubuntu.  That's fine, but does anyone have a generic command-line I could use to connect to my vpn?  The only information I have is the hostname of the pptp server and my password.

Ah, working from home.  So close, but so far away.   Other than this minor nit, no complaints!  Big up to the ubuntu team for a great distro.

---

### Post by halo five on 2005-04-12
OK, figured it out a bit!  Here's what I did to get pptp going on ubuntu 2.05, with a configuration GUI:

1. run Synaptic Package Manager
2. include "Universe" repository (under Settings -> Repository)
3. install pptp package
4. follow the instructions [here](http://pptpclient.sourceforge.net/howto-debian.phtml#install_gui) to install the pptpconfig GUI.  This will resolve a bunch of dependencies automagically (thanks Debian!)
5. sudo pptpconfig and you're off!

On to the next issue!  I can connect to my VPN, pptpconfig connects me and no errors are thrown in the logs.  But - I cannot ssh or ping any of the machines on my work network.  What is strange is that when I attempt to ping a machine on my work's internal network, it resolves the ip correctly, but ping never returns, and I cannot ssh onto any machine.

Anyone run into anything like this before?

---

### Post by halo five on 2005-04-18
> I cannot ssh or ping any of the machines on my work network. What is strange is that when I attempt to ping a machine on my work's internal network, it resolves the ip correctly, but ping never returns, and I cannot ssh onto any machine.

Still haven't figured this one out.  Do I need to manually set up vpn routing?  I didn't have to do this when I was connecting with WinXP, perhaps XP did it automatically?

The machines on my work network have ips of the form 172.16.x.x.

---

### Post by njwetsu on 2005-04-21
I tried to use the [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml) info which referes to a site to add to /etc/apt/sources.lis, but the site doesn't seem to exist anymore "http://quozl.netrek.org/pptp/pptpconfig".  Does anyone know of a place new place or is having the same problem? ](*,)

---

### Post by ernestoongaro on 2005-04-29
Try out my little how-to...
[http://www.ubuntuforums.org/showthread.php?t=28396&highlight=pptp](http://http://www.ubuntuforums.org/showthread.php?t=28396&highlight=pptp)

---

### Post by lonetree on 2005-10-10
I hope this thread has not been closed yet. I also run into this problem. I can connect to the vpn with a vpn tunneling, I can only get resources from my vpn server when i type smb://vpnserveraddress. Can view network, can't connect or ping to any other LAN pcs. What is wrong with my settings?
[U]
Remote Server environment setup [/U]
Remote LAN ip range : 192.168.123.1-100/24
IP assign on vpnclient logon : 192.168.123.201-250
VPN server IP address : 192.168.123.200
VPN server internal IP address : 192.168.123.1
[U]
Local Setup (Client side)[/U]
IP range : 192.168.123.100-200/24
pptpconfig installed

Both sides are connected to the internet with a broadband router.

What other settings do I need?


Hope someone can help me on this

Regards,

---


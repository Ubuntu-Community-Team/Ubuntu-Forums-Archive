---
title: "Cisco VPN Problem"
date: 2006-10-08
forum: General Help
---

### Post by kocmic on 2006-10-08
I recently installed the Cisco VPN client on Dapper. After a couple hours of tinkering I managed to get the vpn working. My problem is that the VPN subsystem isn't starting automatically on reboot. I have to enter the following command after I reboot...

sudo /etc/init.d/vpnclient_init start

How can I get this to happen automaticaly at system start?

---

### Post by BB_Highway on 2006-10-08
I've never managed to get teh Cisco vpn to start automatically at boot on any  distribution, so I don't think that capability even exists.

I just started with Ubunto, and I can't even get the cisco vpn top install. Seems to be problems with the source files and/or headers. How did you get yours installed?

---

### Post by dstaudt on 2006-10-08
I've been able to get the Cisco VPN client installed by adding the 'build-essential' and 'linux-headers-<architecture>' packages from Synaptic, then downloading the tar.gz version of the client, unpacking it and following the readme.  

Just copy the connection *.pcf file that you normally use from your Windows box, and it works fine.

You can enter the VPN service start command into your Session startup commands (Preferences|Sessions), and it will start whever you log into your Gnome session.

---

### Post by xmux on 2006-10-09
Hey how did u install it?? I just unzip the tar.gz package than i tried 

[PHP]sudo ./vpn_install[/PHP]

but nothing happens??? Can u help me how to install??

---

### Post by kocmic on 2006-10-11
yes I used "sudo ./vpn_install"
I did have to play for a long time to get this working.
The other big piece that jumps to mind was installing several versions of GCC via synaptic. Can't remember the name but in the description it states only to use the version for backward compatability.

---

### Post by arunsub on 2006-11-15
I started the VPN and Got the following:
Initializing the VPN connection.
Contacting the gateway at xxx.xxx.xx.xxx
Contacting the gateway at xxx.xxx.xx.xxx (balancing)
User Authentication for XXXXX...

Enter Username and Password.

Username []: xxx
Password []:
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: xxx.xxx.xx.xx
Server address: xxx.xxx.xx.xxx
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled

I thought it got connected, so when I tried to enter the URL for accessing the application from my office server, it says page not found. URL is fine as it works windows cisco vpn. Any idea? None of the sites work too.

---

### Post by arunsub on 2006-11-16
I got vpnc to work. Ignore my previous post.

---


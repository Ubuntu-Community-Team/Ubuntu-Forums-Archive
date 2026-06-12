---
title: "suddenly won't load network"
date: 2022-02-07
forum: General Help
---

### Post by Phil Binner on 2022-02-07
I have 3 Xubuntu computers forming a single user network.  One is the server, another a workstation, and the third a media machine connected to my TV, along with a Sky Box, etc.  This is an nfs network, but it also uses SMB for Windows machines.

All was fine until a few days ago when the media computer stopped opening the network.  I checked as much as possible and decided that something was corrupted, so I completely re-loaded the XUbuntu software.  Once the system was re-installed I opened a terminal and ran

sudo apt install nfs-common

It seemed to install properly.  I have repeated this since and been told that the installed version is the latest.

I edited fstab to include the lines

#  Mount the network Vol01
#
192.168.1.200:/Vol01     /Vol01    nfs   defaults    0  2

It still does not load the network at startup.

The other non server machine, the workstation, is still working fine.   I've checked fstab on that machine and that line  is identical.

The only thing that may have changed during this time is that I reset the router because it was having connection issues, but I think the media machine still worked after that .  I'm not certain of that though; it did go wrong about the same time.

There are other strange things about this.  Although the media machine does not load the network at startup it is connected to the internet, and it is possible to browse for the network share.  When it loads through the browse it loads as smb rather than nfs, however.

Browsing through the network share does not enable the video files to be played, however.  If I browse the share, right click a file and tell it to open with VLC nothing happens.  If I put the network path into VLC it says it cannot connect.  If I copy the file to the local disc and play it from there it works fine, 

Thanking you in advance.

Phil Binner.

---

### Post by el-viejo on 2022-02-07
Since SMB uses user authentication, and NFS uses network based/subnet based authentication, the first thing I'd confirm is what LAN IP address your media machine is pulling. Compare that to the workstation you have that's able to successfully connect to the NFS.

You also may want to reboot both your router and modem if you haven't already. The fact you stated this all started around the time you reset the router makes me think the media machine may have grabbed a DHCP address that doesn't jive with your NFS setup.

---

### Post by Phil Binner on 2022-02-07
Sorted it.

What you said was almost correct, certainly in the right direction.   All the IP addresses were supposed to be fixed, but in resetting the router it decided to change the IP address of the media machine.  I've spent the afternoon installing a (hopefully) better router, and setting all the IP addresses to fixed.  I then edited the /etc/exports file on the server, and it now connects.

Thanks for your help.  I was a bit slow in remembering that the exports file used IP addresses.

---


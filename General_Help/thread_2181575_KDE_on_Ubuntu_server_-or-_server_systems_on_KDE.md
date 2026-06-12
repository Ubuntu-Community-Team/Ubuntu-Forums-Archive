---
title: "KDE on Ubuntu server -or- server systems on KDE"
date: 2013-10-18
forum: General Help
---

### Post by erike4 on 2013-10-18
Does anyone have any wisdom, tales of terror, mindful recommendations or gut feelings on the choice to install the KDE desktop on ubuntu server or add the server functions to Kubuntu?  (btw all systems will be 13.10)
In my case this system would be low use on both sides, as my PC and serving the attached printers, internet connection, plex server and mail hub.  

Thank you in advance....

---

### Post by bab1 on 2013-10-18
> **erike4 said:**
> Does anyone have any wisdom, tales of terror, mindful recommendations or gut feelings on the choice to install the KDE desktop on ubuntu server or add the server functions to Kubuntu?  (btw all systems will be 13.10)
In my case this system would be low use on both sides, as my PC and serving the attached printers, internet connection, plex server and mail hub.  

Thank you in advance....
Ultimately you end up in the same place.  It's easier to just install the desktop version and add the services you want.  If it were a production server you would not need the desktop at all.

---

### Post by erike4 on 2013-10-23
Thank you very much for confirming that issue.  All the literature was old (8-x, 10-x versions of ubuntu) on the subject where they were stating the server version was a tuned system that should be used as base.  Looking into things (from your viewpoint) it looks proper to have a full desktop system as base and then put all the other "server" systems in virtual machines on top of that desktop base system.  I am doing this is because a private cloud system cannot be justified at this time due to overkill, complexity and the low cost now of per thread on multiple core system and the older equipment (room heaters) available to build the cloud.

Thank you again!!

---

### Post by Bucky Ball on 2013-10-23
My concerns are that you are intending to run servers on a not yet/just released, wet-behind-the-ears 13.10 which will be dead and unsupported in nine months. 

LTS versions are intended for servers and production machines and servers should be running the lightest of light DEs, if they're running one at all, and KDE is not that. I would go with xfce4 or lxde if you really want to run a DE on a server and 12.04 LTS, supported until April 2017 (upgrade to 14.04 LTS when it arrives next April for another five years support). 

With 13.10, you will be required to upgrade to 14.04 LTS as that coincides with when it runs out of support anyway.

---

### Post by bab1 on 2013-10-23
> **erike4 said:**
> Thank you very much for confirming that issue.  All the literature was old (8-x, 10-x versions of ubuntu) on the subject where they were stating the server version was a tuned system that should be used as base.  Looking into things (from your viewpoint) it looks proper to have a full desktop system as base and then put all the other "server" systems in virtual machines on top of that desktop base system.  I am doing this is because a private cloud system cannot be justified at this time due to overkill, complexity and the low cost now of per thread on multiple core system and the older equipment (room heaters) available to build the cloud.

Thank you again!!

Why go to the trouble of VM for a simple network.. There is no reason that a machine that is capable of running a KDE desktop shouldn't also be capable of running the typical LAN services such as NFS, Samba and Plex.  If you truly are using this as a server only you can just turn the X-server (and therefore KDE) off after you have set the sever up.

The other hosts won't need the KDE DE.  In fact they don't need any DE to operate.  You don't need the complexity of running multiple instances of the OS ( as VM's).  If you want to run VM's to see how they work that's fine, but you do not have to do that.  The only reasons I can think of for VM's in a home LAN is for experimentation or just to say you can do it. 

I think the points @Bucky Ball brings up are valid.  Ubuntu 12.04 with xfce4 or lxde (Xubuntu or Lubuntu) will be more than adequate for your needs and it comes with long term support.  I have several P3 based Ubuntu 12.04 based machines.  These do not run X-server at all.  CLI only.  The Ubuntu server distro is lightweight by itself.  One of these machines is an Apache Web server along with a Samba server for Windows clients and NFS for Linux clients.  For my needs this works fine.  It is a web development machine.  The other machine is a NAS (Samba and NFS) along with an external disk setup (ext4) that is for backups.  Both of these light weight machines are perfectly suited for a small LAN.

---


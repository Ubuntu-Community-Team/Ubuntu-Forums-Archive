---
title: "Unable to connect or access NAS from PC"
date: 2016-07-07
forum: General Help
---

### Post by GeordieJedi on 2016-07-07
Hi all.

Ok, I've gotten a new desktop PC. I want to connect it to my NAS, so that I can share
files, etc, etc.
The NAS and PC are connected to the same switch, and the modem/router is downstairs.
They are all connected via ethernet

I am really struggling to achieve this, I would really appreciate some help please.


I have done the following / Troubleshooting steps -

01. Created static IPs for my devices (NAS, laptop, desktop) within my internal network.
(using DHCP reservation).

02. Added the hostname of my desktop PC to the hosts, and hosts.allowed files on my NAS.

03. Added the mount points for my NAS shared DIRs on the FSTAB of my desktop PC.

04. Added the hostname of the desktop PC to my NAS (in the GUI enviroment).

05. Added the permissions for the desktop PC to my NAS (in the GUI enviroment on the
NAS).

06. Rebooted both the PCs and the NAS (for any changes to take effect.


Error messages -

01. Error message when trying to access the shares via GUI on the PC

```
An error occurred while accessing '/volume1/photo on Hoth', the system responded: mount: only root can mount Hoth:/volume1/photo on /mnt/photo_share/photo
```


Questions -

01. What am I doing wrong, to stop me from accessing my NAS via my PC ?


Useful details -

NAS = Synology DS410J

Hostnames -
Hoth = NAS
Corellia = PC

PC -
OS:Ubuntu 14.04
Kernel version:3.13.0-85-generic
DE:KDE (version) 4.13.2


Network -
Virgin media cable modem/router (downstairs)
Cat cable run upstairs to switch (upstairs in office)
PCs and NAS connected to switch (upstairs in office)


TIA for any help or advice.

---

### Post by uNoubu8a on 2016-07-07
o/

Thread is a few years old but showing similar symptoms to your issue - [http://ubuntuforums.org/showthread.php?t=2170969](http://ubuntuforums.org/showthread.php?t=2170969)

The tldnr solution from the thread was to install nfs-common and nfs-kernel-server (if not installed);

```

sudo apt-get install nfs-common
sudo apt-get install nfs-kernel-server

```

As I have never played around with a NAS I can't say much from my own experience.



Cheers
404

---

### Post by mastablasta on 2016-07-08
> **GeordieJedi said:**
> 
Error messages -

01. Error message when trying to access the shares via GUI on the PC

```
An error occurred while accessing '/volume1/photo on Hoth', the system responded: mount: only root can mount Hoth:/volume1/photo on /mnt/photo_share/photo
```

look like permission issue on NAS not an Ubuntu issue.

Is the mentioned GUI a webservice in browser?

> 
Questions -

01. What am I doing wrong, to stop me from accessing my NAS via my PC ?


Looks to me like you are accessing NAS, but NAS doesn't allow access to reqeusted file. and i am assuming the error message came from NAS. have you checked with Synology support or documentation as to why the access is blocked or rather it seems as if it is limited to root only (admin)?

if nas was linux this woul dbe easilly solved with chown command on NAS. i think synology uses modified BSD. freeBSD has chown available.

seems like you did ok with the network setup.

---


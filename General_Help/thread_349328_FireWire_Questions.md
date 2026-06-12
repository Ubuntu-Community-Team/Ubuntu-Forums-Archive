---
title: "FireWire Questions"
date: 2007-01-30
forum: General Help
---

### Post by KaeseEs on 2007-01-30
Hey all,

    I'm running a simple home server in my dorm with Ubuntu 6.10 'Edgy Eft'.  I've got a shared directory via Samba, and I have NFS installed but not configured (I've also got Apache, MySQL & PHP running for an unrelated project).  I want to be able to sync files from my laptop (a ThinkPad T60, also running Edgy in a dual-boot config w/ XP) to the server and vice-versa.  

Now, I could boot the lappy into Windows, connect them with an ethernet cable, and sync via Samba, but that takes the fileserver offline while I do the sync (due to some upstream network idiocy, a switch or router is a headache, and a decent one will run me about $40).  So, I've been thinking, my box has an IEEE 1394/FireWire port, and my laptop has a card, if I just grab a cable I should be able to sync real fast that way, right?

Now, my question is, is there a way to see if my FireWire port is recognized by the OS before I go out and buy a cable, and will NFS or something else auto-detect the connection?

Thanks, and merry Ubuntuing!

---

### Post by steefjeqv on 2007-01-30
Hello,

For the last few days I've been trying to connect 2 computers using Firewire and NFS.
It isn't working yet (for me).

Using the information I found on the Ubuntu forum I did manage to configure my Firewire devices as networking devices.

Open up a terminal and type the following command : sudo modprobe eth1394.

Now go to system-management-network and your firewire port should be mentioned as eth1.
You can now configure it as any other network card.

Note : you have to use the modprobe command every time you boot your computer.

Add eth1394 to your /etc/modules file and the firewire port will be recognised automatically at start up.

I hope this rather incomplete explanation helps you setting up your firewire connection.

Following link may be of help too :

[http://www.linux1394.org/]("http://www.linux1394.org/")

Greetings,
Steven

---


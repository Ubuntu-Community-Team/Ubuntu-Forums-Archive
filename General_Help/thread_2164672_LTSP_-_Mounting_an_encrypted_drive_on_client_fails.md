---
title: "LTSP - Mounting an encrypted drive on client fails"
date: 2013-08-01
forum: General Help
---

### Post by ben-Nabiy_Derush on 2013-08-01
We have an LTSP lab running 13.04 with one user who needs to mount an encrypted drive to work from. 
It works fine, if the drive is connected to the server, but not when connected to the client. 

On the client, if I access a root shell, I can see the device. If I issue the cryptsetup command, and mount the resulting device, I can see the device on the client only(not in the ldm session). 

It never makes it to the term session on the server. If I connect a USB thumb drive, it works fine, mounts on the desktop, etc.

Is there some way to make a custom image that could detect the encrypted drive and mount it so that one user could use the information?

---

### Post by TheFu on 2013-08-01
Have you considered providing that user with sudo access to an **extremely specific command** so that the local mount can happen?  Be certain that you specify the exact command - EXACTLY and do not allow setuid/setgid/rootexec properties on the mounted file systems.

$ man sudo
$ man sudoers
should explain everything.

Rereading the issue, I'm almost positive that I don't understand clearly, never used LTSP myself.  Maybe some form of limited, special, sudo command can help?

---

### Post by ben-Nabiy_Derush on 2013-08-01
If I knew what command he would need to issue, that might work. The drive is not seen whatsoever on the server, unless directly plugged into the server, unlike a normal USB drive which automounts to the server.

The whole drive is encrypted with LUKS. When connected to a thinclient, the drive is seen and able to be mounted if I access it through a SCREEN_2=shell, but not seen at all on the ldm side of things.

Does this make sense?

---


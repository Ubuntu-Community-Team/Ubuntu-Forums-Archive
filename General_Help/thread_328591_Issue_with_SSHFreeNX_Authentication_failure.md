---
title: "Issue with SSH/FreeNX: Authentication failure"
date: 2006-12-31
forum: General Help
---

### Post by ImNeat on 2006-12-31
I am trying configure the FreeNX graphical front-end to SSH, but I am running into a problem.  When I try and log in from my client's nxclient I get the error: "Authentication failed for user brandon" - the error has no details.

The connection worked fine until I tried to give my desktop a static IP address.  I think I may have botched a few things up, but I can't figure out what things. I tried changing the desktop back to its old settings, but the connection still wouldn't work.

This is my setup:
NX Server: Ubuntu 6.10 desktop - static = 10.10.10.2
NX Client: ArchLinux 0.7.2 laptop - DHCP = 10.10.10.103
*nxclient/nxnode/nxserver 2.1+ installed on both.
Both are connected to same router.

Notes:
I ran **ssh-keygen -t dsa** from the laptop to create a new public/private key.
I imported the private key through the laptop's nxclient interface.
I saved the public key in **~nx/.ssh/authorized_keys2** on the desktop.

I copied the desktop's **/var/lib/nxserver/home/.ssh/client.id_dsa.key** file to the laptop's **/opt/NX/share/keys/server.id_dsa.key** file.

Does anyone know what else I need to do to authenticate/allow the connection?  Any ideas/opinions will be appreciated.

---

### Post by ImNeat on 2006-12-31
bump

---


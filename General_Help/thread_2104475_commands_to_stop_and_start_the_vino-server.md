---
title: "commands to stop and start the vino-server"
date: 2013-01-13
forum: General Help
---

### Post by swbca on 2013-01-13
The default VNC server (VINO) crashes frequently, and then I have no access to this rack mounted system. I have installed Ubuntu on 2 different computers with the same result. I have also uninstalled VINO and tried Tightvnc Server with the same result.
 
So, I would like to use the gnome-scheduler to stop and start VINO server every few hours but I don't know the commands to put into the scheduler. ( I am not an experience Linux person ) but I have used it for a specific set of tasks for several years.
 
(This system replaces my 5 year old Fedora installation with NX-Server for remote access)

---

### Post by SlugSlug on 2013-01-14
I've found x11vnc better than vino.

I ssh in start it then connect via ssh tunnel.

---


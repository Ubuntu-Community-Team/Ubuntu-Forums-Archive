---
title: "Vmware without X?"
date: 2006-12-13
forum: General Help
---

### Post by Devilotx on 2006-12-13
I haven't checked it out yet, so I figured I'd ask before I start messing with it but, I have a linux file server that runs dapper without X, right now it just does file serving and SSH access for me while I'm on the road.

But I'm interested in running a few other things in Vmware, I've run it in Windows in the past, but my windows computer is just for games these days, I don't want to mess it up again.

but can I install Vmware, ssh in, start a Vmware server so I can VNC or RDP to that server as needed?

Is that possible with Vmware Workstation (or better VMWare player)

I've heard conflicting reports about needing an X server running to start Vmware, I'd like to keep X off if possible.

---

### Post by adamonduty on 2006-12-14
You can install VMWare Server on your server. It runs the virtual machines as a service, so it doesn't need X running. Just connect to the VMWare Server using the VMWare Server Console from another computer.

---


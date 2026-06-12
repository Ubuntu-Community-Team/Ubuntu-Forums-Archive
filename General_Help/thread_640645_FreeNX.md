---
title: "FreeNX"
date: 2007-12-14
forum: General Help
---

### Post by mchaley on 2007-12-14
What problems have people run into with this? I'd love to get the bugs worked out of this... i'd love to impliment this on my servers :D 

daflame has been working on updating freenx:

First of all, yes you can use the NoMachine Windows client to log on. I have an employee that log onto a Kubuntu machine in the office every day from his Windows machine at home using the NoMachine client. In fact, the nxclient in my tutorial is from NoMachine.

Currently the only major issues remaining are:
1) Shared folders don't translate the names correctly
2) VNC Proxy doesn't work (you can get around this by setting up VNC server yourself and using a VNC client with a custom connection in NX).

The shared folders thing is a real pain, but you can access them yourself via sftp.
I fixed the nxdialog issues by setting up a patch to match the FreeNX trunk repos with their fixes.

In case you haven't seen my site, here it is:
[http://ubuntuforums.org/showthread.p...ghlight=freenx](http://ubuntuforums.org/showthread.p...ghlight=freenx)

---

### Post by abhi.datt on 2007-12-17
Has anyone tried x2go on Ubuntu??

---

### Post by daflame on 2007-12-19
> **abhi.datt said:**
> Has anyone tried x2go on Ubuntu??

I haven't tried it, but it appears they use the NX 3.0 libraries just like FreeNX.  Apparently they don't plan on being compatible with nxclient.  This could be more difficult if you want Windows clients out of the box.

---


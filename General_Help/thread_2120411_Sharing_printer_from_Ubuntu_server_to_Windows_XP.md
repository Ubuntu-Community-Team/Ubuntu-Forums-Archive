---
title: "Sharing printer from Ubuntu server to Windows XP"
date: 2013-02-26
forum: General Help
---

### Post by NautiusMaximus on 2013-02-26
I've been trying to set up printer sharing on an Ubuntu 12.04 server, so that I can print to the printer from a Windows machine on the same network.

This has proven quite tricky. I have managed to print a test page from the server, and that works just fine. I can share the printer with a Windows XP machine, but in the process of adding it to the Windows machine, it asks me for a driver. If I choose a generic text-only driver at that stage, it works, but obviously with rather limited functionality. If I choose the correct HP driver, then it doesn't work at all.

Now, before I put further effort into troubleshooting this, I'm just wonder if there is any point?

If, during the installation process on the Windows machine, I need to install the drivers anyway, then why would I bother to install the printer on the Ubuntu server at all? I've been used to installing printers on a Windows server, and if that's set up right, then they can just be added to the Windows client machine without needing to install drivers, so that's a good way of doing things if there are a few client machines on the network. However, if I'm going to have to install drivers on each client machine anyway, then wouldn't it be just as easy to install the printer directly on each client machine? The printer is plugged into the LAN, so it's visible from all the client machines.

Am I missing something here, or should I just abandon my attempts to install the printer on the server?

Thanks
NM

---

### Post by NautiusMaximus on 2013-02-28
Bump?

---

### Post by Jerry N on 2013-02-28
Maybe it is because I am old and dumb but I have had very poor luck trying to share a printer connected to a Linux machine with a Windows computer on the network.  Usually when I got it to work it didn't work for very long.  On the other hand, sharing a printer connected to a Windows computer with Linux computers on a network has worked well for me.  I would suggest connecting the printer directly to the target Windows computer and going through the full install.  Then connect the printer to the Linux computer and go through the sharing process.  It has been some time since I did this so I am not able to give specifics.  My latest printer is ethernet connected and eliminates the Windows vs Linux connection problems.

Jerry

---

### Post by NautiusMaximus on 2013-03-04
Many thanks for that, Jerry. I'm beginning to conclude that there's probably not really anything to be gained from installing the printer on the server: just install separately on each client machine.

---


---
title: "Installing reduced Ubuntu for remote or VM?"
date: 2006-12-14
forum: General Help
---

### Post by theosib on 2006-12-14
What I want to do will apply equally well to virtualization and networked computers.  What I would like to do is make an install of Ubuntu that does not start a local X server but instead points the DISPLAY at some other computer, already running a desktop and X server.  At the same time, all of the X11 stuff does need to be installed.  This way, I don't need the overhead of an X server on the guest OS or compute farm machine.  I don't want to use XDM or something like that, because I don't want the remote or guest machine to provide a desktop, just run compute-intensive apps and some X11 tools.

What is the easiest way to do this?

One thing I thought of was just doing a full install and then figuring out how to disable X11, but there's got to be more elegant ways to install and more elegant ways to integrate things with another desktop.  Also, I'd like to see if I can keep the kernel from loading modules for devices I don't need.

Thanks!

---

### Post by adaptr on 2006-12-14
> **theosib said:**
> What I want to do will apply equally well to virtualization and networked computers.  What I would like to do is make an install of Ubuntu that does not start a local X server but instead points the DISPLAY at some other computer, already running a desktop and X server.
That's not how it works.
You can set up a server to accept incoming XDMCP requests, so remote clients (running an X server, heh) can connect to its display manager.
The client-side capability is enabled by default in Ubuntu; just choose the relevant option from the login menu (bottom left of screen).

> At the same time, all of the X11 stuff does need to be installed.  This way, I don't need the overhead of an X server on the guest OS or compute farm machine.  I don't want to use XDM or something like that, because I don't want the remote or guest machine to provide a desktop, just run compute-intensive apps and some X11 tools.You'll have to tweak the server some to get it NOT to install an X server, as that is the default for any X package in Ubuntu I have yet seen.


>  What is the easiest way to do this?The easiest way would be to just install gdm on the server (this will install some 350MB of cruft), and then **enable** remote connections via XDMCP and **disable** the local X server.

>  One thing I thought of was just doing a full install and then figuring out how to disable X11, but there's got to be more elegant ways to install and more elegant ways to integrate things with another desktop. More elegant == more time.
You'd have to install the specific packages you want, and override all dependencies you don't need.
You'll have to figure out which ones these are first, of course.

> Also, I'd like to see if I can keep the kernel from loading modules for devices I don't need.That's simple - just disable them from loading.
I suppose you mean all the USB and plugnplay stuff - I'm not sure that much is loaded by default on the server version.

---


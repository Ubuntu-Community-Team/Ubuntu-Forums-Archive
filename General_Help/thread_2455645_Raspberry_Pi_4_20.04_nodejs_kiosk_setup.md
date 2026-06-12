---
title: "Raspberry Pi 4 20.04 nodejs kiosk setup?"
date: 2020-12-24
forum: General Help
---

### Post by bmrx2 on 2020-12-24
Hey all,

Recently bought a new pi4 and with all the extra memory I have (1GB -> 8GB) I'm hoping to use it for more than just a home webserver. Currently it's running Apache, Mysql, PHP and I want it to continue doing so.

I have the pi hooked up to the official raspberry pi 7" touchscreen and would like to run node.js apps on the screen in fullscreen, (whatever those apps might be). I'm not too interested in having a desktop environment, in my "research" I've found that "kiosk" mode is possible via chromium and/or X11.

But I'm way out of my element here and have no idea what tutorial to follow, currently running just CLI so I don't have a desktop installed of any sort.

Does anyone know of any good articles/tutorials to follow that will help? Some point at setting up config files for something called xsessions, but I have no idea what that is or where I get it. Others talk a bit about x11, but all of them seem to expect that I have a desktop environment installed already... I don't know what one I should install if any.

EDIT/ I should add I've found Mir-Kiosk: [https://snapcraft.io/mir-kiosk](https://snapcraft.io/mir-kiosk)
But I'm having trouble finding out if I can run nodejs/electron apps in it.

I've also just found this: [https://ubuntu.com/tutorials/electron-kiosk#1-overview](https://ubuntu.com/tutorials/electron-kiosk#1-overview)

So I might just jump into mir-kiosk and see if this is what I am looking for.

Any resources on what I'm looking for are greatly appreciated.

---

### Post by TheFu on 2020-12-24
You should get another microSD storage device and put a light desktop install onto it. That would be the easy solution. Everything else will be hard.  If you prefer pain, go ahead and try to add the GUI/Desktop with X11 to your existing install, but expect lots of failures.

As for putting lots of different things onto a single computer, this is a bad idea for a number of reasons.  This is why virtualization became so popular. It was a way to compartmentalize different servers and dependencies of those servers into different "virtual machines."  Over the decades, VMs have become a staple for every IT department. Where I worked in 2005, deploying onto a VM was mandated with the only exceptions being due to special hardware requirements.  

Web servers, email servers, web-app servers and virtual desktops would each be placed into different VMs.  These days, people use Linux Containers as the way to compartmentalize daemon services like web apps and email.  I don't think raspberry pi's support a VM hypervisor (or if they do, it is alpha code), but all Linux systems the last 15 yrs have supported Linux containers, so creating a different container for each type of daemon would be smart to keep the dependencies from unwanted interactions.  After all, there will be different versions of php required for different webapps. Same for Node.js stuff. Keep each inside a different container.

I'm not a fan of Electron stuff. Much too bloated. You'll see.  When I look at Node stuff, I see similar mistakes made that Perl and Python was making in the 1990s, but if you know javascript, I suppose every solution has to include some of that stuff.

X11 has a long history on Unix workstations and with Linux. There is a wikipedia article about it from an overview standpoint.  Smart people have spend years understanding X11, so don't expect to pick it up in a day or two.  I was sent to 2 full weeks of training just on X11 a few decades ago and that only provided an introduction to the ideas with a little C programming included.  I probably have the 8 X/Windows books (350-500 pgs each) from that class somewhere.
X11 is short for X11R? ... I think we use X11R6 today.  Before that was X11R5 and X11R4 ... you get the idea. From a high level standpoint, 
**X11 == X/Windows == X they are all referring to the same toolkit for displaying GUI programs in a networked way.**  X is a client/server architecture.  The server and client can be on the same machine, different machine, inside virtual machines or inside containers. Mix and match the clients in almost any way you like.  The X/Server runs on the machine where you have a keyboard, mouse and monitor.  X/Clients can run local or remote. Any number of X/Clients from any number of remote systems is possible. Right now, I'm connected via X11 with about 20 X/Client programs running running on about 10 systems - some are virtual and some are physically different machines. All X/Clients talk to the X/Server using UDP and IP network connections.  Basically, each window is a different X/client running on a remote system.

The real key to X/Windows client-server architecture is that it works exactly backwards from what 99.999% of other Client/Server architecture systems do.

Clear as mud?

Specific X11 details are layer specific and different DEs in Linux have added layers to hide some details and capabilities that X11 has provided for at least 40 yrs.  And just to make it more fun for you, X11 is being replaced by a different display server called Wayland.  Wayland is trying to address performance and security issues that the networked-X11 architecture has always had. Wayland expects direct access to a GPU.  X11 doesn't.  Wayland doesn't support networked client programs running remotely, but for the average home Linux user, when they think of running programs remote, they think that RDP or VNC are the methods to use (which they are NOT!).  Wayland has/is adding a remote client capability to appease people like me, whose workflows are ingrained with remote applications.  For example, I run thunderbird, a think email client, on a remote system. I don't run it on the system I'm sitting behind.  Same for Firefox - it runs on a different, restricted, remote system for security reasons. This way I get the performance and CPU of those other computers doing work for the heaviest programs I run and each doesn't slow the system I'm actually sitting behind down.

X11 is CPU architecture agnostic. It doesn't care if the X/Client program is running on MIPS, Intel, Arm, or any other type of CPU. It only cares that the X11 protocol is used.  What this means is that you don't actually need to load a desktop onto your Raspberry Pi to make use of the RAM and CPU.  You just need a local X/Server and a few X/Client programs running on the r-pi to make use of it.

However, if you want high-end gaming or streaming video/audio to be sent from an X/Client on the r-pi to your local machine, just know that X11 protocol wasn't designed for video streaming 40 yrs ago.  It was created for email, spreadsheets, code editing and typical business office applications. I've used it on 5 continents, usually via x2go, but not for streaming video.

Mind blown yet?  [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) has specific examples of running X/client applications remotely.  I should probably update it a little, but the core stuff is still correct.

---


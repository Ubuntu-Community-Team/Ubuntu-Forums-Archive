---
title: "run my desktop over network"
date: 2007-02-11
forum: General Help
---

### Post by Space Cowboy on 2007-02-11
This isnt so much an Ubuntu help request as general computer help, but whenever I ask questions here they're always answered quickly and politely. I really appreciate that by the way.

Anyways, I have this lunky desktop that I really only use for data storage and internet connection (I dialup with the desktop and then use that connection on my laptop over the network, and yes if I could get any better internet than dialup I would, but I can't) and it has a lunky screen that takes up alot of space. I know people do this all the time, but I was wondering how I can control this desktop with my laptop, since one, I could ditch the bulky screen and save space, but two, conveniently control both computers.

I am not very learned when it comes to computers and networking, but my first idea, which seems the simplest, would be to set up a VNC server. This seemed easiest because right now the desktop is running Windows (I would install Ubuntu but theres always a kernel panic when booting the live CD, and I havent gotten around to figuring that one out yet) and I could easily set up a VNC, set it to auto log in, and have the VNC server set to start on log in, but I thought, theres always unexpected windows issues and one day it might not work out and I might need to hook up the screen, keyboard and mouse again.

I assume there is a better way to go about doing this, so, any suggestions? I would prefer little change to the system (not having to install another OS and back up the huge HDD) but I am willing to, plus windows is getting a little slow on there anyways so I figure its teeming with something and about time to reformat.

Any help appreciated.

---

### Post by Marsolin on 2007-02-11
I'd do what you are already thinking.  I have a Windows system running without a monitor and run TightVNC Server on it.  It's a free program you should be able to find with a quick search. I suggest giving this system a static IP address to save you any headaches in not being able to locate it.  I always log into mine using the IP address instead of the computer name because it is faster.

You should already have a VNC client in the default Ubuntu install.

---

### Post by Space Cowboy on 2007-02-12
> **Marsolin said:**
> I'd do what you are already thinking.  I have a Windows system running without a monitor and run TightVNC Server on it.  It's a free program you should be able to find with a quick search. I suggest giving this system a static IP address to save you any headaches in not being able to locate it.  I always log into mine using the IP address instead of the computer name because it is faster.

You should already have a VNC client in the default Ubuntu install.
Thank you then, for now that is what I will do.

---


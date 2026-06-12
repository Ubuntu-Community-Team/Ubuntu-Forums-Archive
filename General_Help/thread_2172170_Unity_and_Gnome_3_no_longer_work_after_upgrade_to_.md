---
title: "Unity and Gnome 3 no longer work after upgrade to 13.04 says graphics card is no good"
date: 2013-09-03
forum: General Help
---

### Post by Corey Goettsch on 2013-09-03
Hello,

I recently upgraded from 12.10 to 13.04, and after the upgrade, neither Unity nor Gnome 3 works.  When I run Gnome 3, it goes to fallback mode.  When I attempt to use Unity, the desktop and wallpaper appear, but nothing else happens.  Also, when I run Gnome fallback mode, I cannot access programs I've minimized since my programs don't appear on the bottom bar.  I am able to open a terminal in Unity.  I attempted to reset compiz and unity as some other threads suggested.  This did not work.  It told me that my hardware does not support Unity.  This seems strange since I've never had any problems running unity, and I even run intense 3d accelerated games like Amnesia: The Dark Descent.  My computer is a Dell Inspiron 1545 with a 2.1 GhZ Intel Dual-Core CPU with integrated graphics.  Also, it mentioned something of a segmentation fault.  If it helps, I can provide all of the output of the terminal.  Would someone please help me fix this?  I've been using MATE, but I'd prefer to use Unity again.  

Also, I can't run the software updater.  It says that it cannot access the internet or something to that effect.  I do have internet access.  When I run sudo apt-get update, it says that it can't reach some archives: [http://ppa.launchpad.net/amith/ubuntutools/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/amith/ubuntutools/ubuntu/dists/raring/main/binary-amd64/Packages) and [http://ppa.launchpad.net/amith/ubuntutools/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/amith/ubuntutools/ubuntu/dists/raring/main/binary-i386/Packages).  I'm not sure if this is connected to my inability to run updates.  

Thank you for all of your help!  I would be grateful for any advice anyone has.  

Sincerely,

Corey Goettsch

---

### Post by Corey Goettsch on 2013-09-03
Well, a quick update:

I did get my updater issue solved: I just had a broken ppa in my system: that amich/ubuntutools one was causing problems.  

However, I have not yet solved my Unity problem.  I thought it might be a driver issue, so I installed the latest Intel graphics drivers using the intel-graphic-driver-install tool.  This did not solve the problem.  

I also tried to launch some 3D games, and none of them came up: I tried Amnesia, Darwinia, and EDGE.  When I tried to open EDGE, it said that OpenGL could not be initialized, so maybe I have an open GL problem?

---


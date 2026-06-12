---
title: "Share printer over network"
date: 2012-11-08
forum: General Help
---

### Post by glennric on 2012-11-08
Where are the settings to share a printer over a network or view shared printers?  I found these settings via [http://localhost:631/](http://localhost:631/), but these used to be available via the gnome print settings GUI.  Where are they now?  They are not available via System Settings->Printers.

---

### Post by gifford on 2012-11-08
If you go to system settings(and I am assuming the printer is already set up on the network) and go to printing, when the printer icon comes up, right click for properties and the settings to share the printer.

---

### Post by glennric on 2012-11-08
The printer is connected to the local computer, and I want to set it up so that it is seen over the network.  That is how it was set up before I did an upgrade to 12.10.  That setting must have been lost during the upgrade.

Right clicking on the printer icon in "System Settings->Printers" does nothing.

---

### Post by kurt18947 on 2012-11-09
The new printer app is not an improvement(to be kind).  Fortunately, you can still install the old one.  It's called "system-config-printer".   Install using the software center or Synaptic then  alt-F2 and type the package name.  It should launch.

---

### Post by gerowen on 2012-11-09
Just go to the printer dialog, then go up to the top where the menus are, click "Server" then "Settings".  It's pretty easy and straight forward.  That's all I've used on all my Ubuntu machines and have never had to really do anything manually other than check the boxes in this dialog as I deem appropriate.

The mini-webserver that runs on port 631 is handy if you're using a Windows PC and need to add it manually using the http address of the printer.

---


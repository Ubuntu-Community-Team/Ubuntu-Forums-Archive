---
title: "How to configure usb automount via ssh"
date: 2019-10-07
forum: General Help
---

### Post by aenye on 2019-10-07
Hi!
Need help with automount in xubuntu.
Previosly i disabled auto-mount via GUI (in gnome: Edit -> Advanced -> Configure -> first 3 checkboxes is unselected)
Now i need to return these settings, but idk how...
How i can return these settings, if i can connect to this machine only via ssh?
Can someone help me?

P.S. Sry if my eng is bad, im ukrainian... If u don't understand my question - pls, specify

---

### Post by slickymaster on 2019-10-07
Thread moved to **General Help** which is a better venue for it.

---

### Post by TheFu on 2019-10-07
Use ssh X11 forwarding and run the config program.

```
ssh -X userid@remoteIP "xterm -sb"
```
If an xterm doesn't show up on your local machine in a few seconds, then X11 forwarding might not be enabled in the sshd_config file.  

Sorry, I don't use Gnome and don't know the actual name of that program.  Also, I don't use the GUI much for any settings. "automount" is a specific tool, which I seriously doubt Gnome is actually using.  On Linux, most people use **autofs** instead of automount.  [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)  This isn't tied to any GUI program and works regardless of which GUI or not having any GUI.

Welcome to the forums.

---

### Post by Skaperen on 2019-10-07
you might try a package called [COLOR=#0000cd][FONT=courier new]**usbmount**[/FONT][/COLOR].  google led me to [http://ubuntuguide.net/enable-automount-usb-drivers-on-ubuntu-server](http://ubuntuguide.net/enable-automount-usb-drivers-on-ubuntu-server)

---


---
title: "Network Manager"
date: 2007-09-17
forum: General Help
---

### Post by coolth3 on 2007-09-17
I somehow deleted the Network Manager applet from my panel.  Now , I can't seem to find the applet anywhere (Well, anywhere in the GUI).  Network Manager is running and connecting to my wireless router at home as usual, except that I can't see the applet telling me the signal strength and other networks available, etc (whenever it connects to my router a notification appears telling me it has done so).  I really like the Network Manager applet, it comes in handy since I take my computer to school and it makes it easy to switch on and off of different wireless networks that are available.  How do I get the applet back? I already tried uninstalling the Network Manager and installing it again through the Update Manager and I even "completely" removed the Network Manager using the Synaptec Package Manager and installed the application again.  Any help will be appreciated.

---

### Post by dcstar on 2007-09-18
> **coolth3 said:**
> I somehow deleted the Network Manager applet from my panel.  Now , I can't seem to find the applet anywhere (Well, anywhere in the GUI).  Network Manager is running and connecting to my wireless router at home as usual, except that I can't see the applet telling me the signal strength and other networks available, etc (whenever it connects to my router a notification appears telling me it has done so).  I really like the Network Manager applet, it comes in handy since I take my computer to school and it makes it easy to switch on and off of different wireless networks that are available.  How do I get the applet back? I already tried uninstalling the Network Manager and installing it again through the Update Manager and I even "completely" removed the Network Manager using the Synaptec Package Manager and installed the application again.  Any help will be appreciated.

Try reinstalling the **gnome-netstatus-applet** package.

---

### Post by walkerk on 2007-09-18
```
nm-applet --sm-disable
```

---

### Post by fragos on 2007-09-18
Systen-> Preferences-> Sessions-> "Startup Prgrams Tab".  Make sure "Network Manager" in the list is checked.  If the right click that line and select edit, the command parameter should be "nm-applet --sm-disable"

---


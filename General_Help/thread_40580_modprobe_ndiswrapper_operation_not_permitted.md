---
title: "modprobe ndiswrapper operation not permitted"
date: 2005-06-09
forum: General Help
---

### Post by mephisto56 on 2005-06-09
I've followed the ndiswrapper howto from the wiki and everything works fine until the 'modprobe ndiswrapper' step. There it gives me this error message: 'modprobe ndiswrapper (/lib/[...]): operation not permitted).
Any ideas regarding this?

---

### Post by Joeb on 2005-06-09
What happens if you try:  sudo modprobe ndiswrapper  ....?

---

### Post by mephisto56 on 2005-06-10
[QUOTE=Joeb]What happens if you try:  sudo modprobe ndiswrapper  ....?[/QUOTE]

Actually the same.

---

### Post by az on 2005-06-10
Post the output of
sudo ndiswrapper -l

and

dpkg -l|grep ndiswrapper

---

### Post by mephisto56 on 2005-06-10
[QUOTE=azz]Post the output of
sudo ndiswrapper -l
[/QUOTE]

bmcw15 invalid drivers
[some similar invalid drivers]
GPLUS invalid drivers [the one I tried to install]
windows_drivers invalid drivers [the map my windows driver is in]

[QUOTE=azz]
dpkg -l|grep ndiswrapper[/QUOTE]

ii ndiswrapper 0.12+1.0rc2-1 source for the ndiswrapper linux kernel module
ii ndiswrapper 0.12+1.0rc2-1 userspace utilities for ndiswrapper

---

### Post by az on 2005-06-10
It would seem that you need to remove the drivers you have installed and install good ones.

---

### Post by mephisto56 on 2005-06-11
Uninstalled all drivers. Found out only win2000 drivers seemed to work (that is: give me a proper driver installed message after ndiswrapper -l)... until I rebooted. Now ubuntu won't boot me into the desktop anymore and somewhere half screen hangs a ndiwrapper load error.  ](*,)

---

### Post by az on 2005-06-11
Boot into recovery mode and remove the ndiswrapper alias to prevent the module from loading on boot.  Sorry,  I do not know the exact file right now....


man ndiswrapper (the -m option)

---

### Post by mephisto56 on 2005-06-13
Recovery mode also hangs. I guess it will be a reinstall. :(

---

### Post by fxer on 2005-06-14
There has to be 50 threads in the forum with the same "modprobe operation not permitted" error, and they all have one thing in common:

No one on this forum has a real answer :)

I've gotten to the same point as you, where ndiswrapper -l says "driver installed, hardware detected", but when you try to modprobe ndiswrapper, ubuntu craps out and says the operation isn't permitted. 

When you have the permissions to modprobe, have the hoary provided packages for ndiswrapper, why on earth would it just take a dump like it is doing for, apparently, lots of people?

Some people claim to have success building ndiswrapper from scratch, but just as many people have problems with that method.

I've been trying to get a linksys WUSB11 v2.8 working for 5 or 6 hours now, to no avail, but it's still been fun, learned a lot in that time :)

Well, sorry I don't have the answers for you, but neither does anyone else on this forum (or other forums), I've read every post on the topic and it's all just clutching at straws, maybe when 5.10 comes out wireless will be more useful :)

---

### Post by GeneralCody on 2005-06-14
I have used NDISwrapper with usb nic's and sometimes it crashes with the ehci_hcd module for usb 2.0.

If I sudo rmmod ehci_hcd first, then sudo modprobe ndiswrapper, all works fine.
Seems to bee some resource conflict. If u have stuff using usb 2.0, and u do the rmmod, the PC might freeze up.

Haven't had time to dig into this, but it might be a quick hack to solve the problem to load the ndiswrapper module before ehci_hcd.

U can get good information if u tail the messages log while doing the modprobe:
tail -f /var/log/messages.

I compiled and installed the ndiswrapper from source.
Might be a good idea to use the latest.

---

### Post by fxer on 2005-06-14
As a side note, anyone with the linksys WUSB11 2.8 [this post](http://www.ubuntuforums.org/showpost.php?p=152579&postcount=12) may get you where you need to go

---

### Post by mephisto56 on 2005-06-16
It's all a bit annoying since no internet means no linux. But I keep trying whenever I have some spare time.

---

### Post by mephisto56 on 2005-06-16
The error codes from boot:

code: bad EIP value <3> ndiswrapper (wrapper_init:1494): loadndiswrapper failed (11)

and finally hangs after 'starting hotplug system'. 

I tried to load with the 'nohotplug' option but that doesn't change anything.

---


---
title: "Network-Manager screws up my system."
date: 2005-10-16
forum: General Help
---

### Post by MetalMusicAddict on 2005-10-16
Im not exactly sure how its supposed to work at startup but when I reboot after I install it, the gnome-panels are blank. Theres no "right-click" on the desktop and I have no network conectivity. The only thing that saved me is my StaterBar that has a Terminal so I can apt-get remove network-manager.

Happens every time. I would take a screenshot but I couldnt do that either.

A shame because network-manager looks great. This will be my only real problem installing a app since Warty.

Any ideas?

---

### Post by akseli on 2005-10-24
[QUOTE=MetalMusicAddict]Im not exactly sure how its supposed to work at startup but when I reboot after I install it, the gnome-panels are blank. Theres no "right-click" on the desktop and I have no network conectivity. The only thing that saved me is my StaterBar that has a Terminal so I can apt-get remove network-manager.

Happens every time. I would take a screenshot but I couldnt do that either.

A shame because network-manager looks great. This will be my only real problem installing a app since Warty.

Any ideas?[/QUOTE]

Make sure that you are installing version 0.4.1 ... I am aware that there is a version 0.5.1 available but it seems that it causes more problems than it fixes... I have had no problem with Breezy and Network-Manager... (knock on wood)
I'd recommend doing this install through Synaptic so you can make sure that you are installing the correct version.

Good luck!

---

### Post by MetalMusicAddict on 2005-10-24
I have a couple of issues.

1. On boot-up when the system is "Configuring Network Interfaces" it times out and fails.

2. When I log in and the desktop starts to come up, everything freezes. Nothing on panels and my network monitor desklet shows no IP nor activity.

3. It takes forever for it to connect then I have to manually input the password for the keyring because its locked.

Seems that this should replace whatever currently handles networks and implimented on lower levels. I wished this worked faster for me. It is very nice when everything finally loads.

---

### Post by MetalMusicAddict on 2006-01-09
I still have these same problems when I try to use Network-Manager.

Is it not supposed to have a connection on startup? Now, I have to wait till everything comes up to make a connection.

Can anyone point me to some info on the development of Network-Manager?

---

### Post by nocturn on 2006-01-09
[QUOTE=MetalMusicAddict]I still have these same problems when I try to use Network-Manager.

Is it not supposed to have a connection on startup? Now, I have to wait till everything comes up to make a connection.

Can anyone point me to some info on the development of Network-Manager?[/QUOTE]

I have the same issue with it... it works more or less, but no connection before log in and somewhat slow after that.  Maybe gtkwifi, netapplet or wifi-radar are better for you, though I did not find them suited either.

---

### Post by matthias_k on 2006-08-13
Anyone figured out yet how to open a connection before the GNOME panel loads?  I can't even use NTP sync while booting, because there's no open connection while booting.

---


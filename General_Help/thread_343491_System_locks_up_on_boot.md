---
title: "System locks up on boot"
date: 2007-01-21
forum: General Help
---

### Post by mertlin on 2007-01-21
I have set up Ubuntu Edgy on my dell latitude c840. At first it worked fine but now when i boot and gnome loads, the system completeley freezes. Nothing responds. Just before restarting I had been configuring ndiswrapper and had installed some package updates. Other than that, nothing has changed that might have caused the lock up.

When I log into failsafe gnome, gnome loads and displays a box with the error and then blanks screen and gdm reappears.

I logged into root on a terminal session to look at /var/log/messages and i find:

```
gnome-power-manager: Critical error: This program cannot start
 until you start the dbus session service. This is usually started automatically
 in X or gnome startup when you start a new session.

```

Any suggestions?

---

### Post by kelboy on 2007-01-24
I'm also getting the exact same error, the only sessions I'm able to use is the failsafe gnome?

anybody?

---

### Post by Draeith on 2007-02-04
I also had this same problem, and after much cursing I found a solution that worked for me.  Somehow I had manged to really mess up /etc/network/interfaces.  It was missing the 

> 
# The loopback interface
auto lo
iface lo inet loopback

part in interfaces.

I scrubbed it clean, added the above as well as my eth0 settings (ignoring my wifi card for the time being), saved and rebooted.  Viola.

---


---
title: "Laptop Started taking ages to boot"
date: 2008-04-19
forum: General Help
---

### Post by gavinjb on 2008-04-19
Hi,

The other day my Laptop completely locked up (no keyboard or mouse access) so I had to do a unsafe restart, since then Ubuntu has been taking ages to startup (the boot progress bar get to about 1/5 of the way and stops for a couple of minutes), the lockup of the Laptop might be a complete red herring as I have also recently installed and uninstalled several software packages, but I cant see why this would cause a problem.

Anyone with any ideas?



Gavin,

---

### Post by angry_johnnie on 2008-04-19
Have you tried booting without a splash, just to see what's taking so long.  

I had a similar issue once, and it turned out to be Ubuntu trying to configure the network during boot, which is really not needed, and can be disabled.

Try this:

```
gksu gedit  /etc/network/interfaces
```

and change it, so it looks like this:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


It could be that.

---

### Post by ezak on 2008-04-19
If the problem continues and all else fails, I would suggest you run: sudo dpkg-reconfigure --all

Note, this will take some time.

Most of the options are safe to leave at default, and not all of them are self-explanatory. But this way you can reconfigure your entire system the way you want and fix your slow startup problems as well.

---


---
title: "Simple Network Script Please"
date: 2007-03-10
forum: General Help
---

### Post by Irony on 2007-03-10
I'd like to make a script in my;

[PHP]~/.gnome2/nautilus-scripts[/PHP]

folder which does;

[PHP]sudo ifup eth0
sudo ifdown eth0[/PHP]

I find that Edgy frequently doesn't detect my network so I have to manually do this in terminal.

If someone with programming skills could devise such a script I would be grateful.

---

### Post by yopnono on 2007-03-10
Try this application. It's a network manager

[http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/)

---

### Post by Irony on 2007-03-10
I'm on a wired network - I forgot to mention that it is only on boot-up that it frequently doesn't connect; once I've done up/down it connects.

---

### Post by strabes on 2007-03-10
```
sudo apt-get install network-manager network-manager-gnome
```

You should also disable the gnome network manager from handling your interfaces.

```
sudo gedit /etc/network/interfaces
```
comment out (with #) all the interfaces except  "iface lo inet loopback"

This is what my /etc/network/interfaces file looks like:

> 
#auto lo
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


save the file (ctrl+S) and restart networking:

```
sudo /etc/init.d/networking restart
```

Then run network-manager:

```
network-manager-gnome &
```

---

### Post by Irony on 2007-03-13
Thanks for reply I'll give it a go.

---


---
title: "interfaces configuration.. where am i wrong?"
date: 2006-11-23
forum: General Help
---

### Post by a.d.gardiner on 2006-11-23
hi guys,

im trying to set my ip statically with the settings below in interfaces. I want a static IP (192.168.0.39) because im running an apache server.

```

auto eth0
iface eth0 inet static
address 192.168.0.39
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1

```

Thing is the machine works fine and sees my router for internet at 192.168.1.1 when its using dhcp, but with the above settings i get the error below when i try to restart networking with "sudo /etc/init.d/networking restart"

```

shop@shop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... SIOCSIFNETMASK: Invalid argument
Failed to bring up eth0.

```

any ideas where im wrong?

cheers,

alex

---

### Post by Jimmey on 2006-11-23
Instead of restarting networking, you could just try > sudo ifup eth0. But that will still throw the same error.

Do you have Xorg installed? Or Gnome?

Try > ifconfig eth0 gateway 255.255.255.0

Which might not work..I'm at college at the moment, no way of checking :-P

If it doesn't, try > man ifconfig

---

### Post by a.d.gardiner on 2006-11-23
Im using Xfce on xubuntu. Mainly went for it because i have really nasty old hardware. to be honest im very new to linux, would gnome or xorg make a difference to configuration stuff like this. i thought they were only window managers? :-|

---

### Post by Jimmey on 2006-11-23
Yeah. I was asking to see if there was some method by which you could condigure the networks via GUI. If you can, I'd advise it. :-P

---

### Post by cambei on 2006-11-23
> **a.d.gardiner said:**
> hi guys,

im trying to set my ip statically with the settings below in interfaces. I want a static IP (192.168.0.39) because im running an apache server.

```

auto eth0
iface eth0 inet static
address 192.168.0.39
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1

```

...

```

shop@shop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... SIOCSIFNETMASK: Invalid argument
Failed to bring up eth0.

```


Your netmask is wrong for what you want your gateway address to be. You are saying you are using a class C 255.255.255.0 subnet mask, and that your host should be one the 192.168.0.0 network, but your gateway is on the 192.168.1.0 network.

It should be something similar to:
```

auto eth0
iface eth0 inet static
address 192.168.1.39
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

This way you do not have to change the settings on your gateway device.

I assume this is why you receive the error message about the netmask argument being invalid.

---

### Post by a.d.gardiner on 2006-11-24
yep bang on... 192.168.1.39. Duh!

sometimes you can't see the wood for the trees.. probably more appropiately my stupidity.

thanks all ;)

---


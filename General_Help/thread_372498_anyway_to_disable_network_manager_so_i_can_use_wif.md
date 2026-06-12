---
title: "anyway to disable network manager so i can use wifi-radar?"
date: 2007-02-28
forum: General Help
---

### Post by pixeldotz on 2007-02-28
so i finally got my broadcom 4311 working flawlessly using ndiswrapper.

here's my only problem now, i want to use wifi-radar to manage my network settings but network manager keeps taking control. whatever settings i have network manager take over from wifi-radar. wifi-radar sees my access point since it gives me the option to connect, but won't connect to it. so i'm thinking it's the default network manager that's messing around with all this.

any suggestions? also, will wifi-radar manage my wired connection aswell? (i'm not at home with my laptop currently to test it)

thank you, any help is greatly appreciated.

---

### Post by g8m on 2007-02-28
There's a file in /etc/network.

Interfaces. 
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet dhcp

Doet it work if you put '#' pound-signs for those. It works for me if I want to use network-manager-gnome instead of the default network-manger.

---

### Post by pixeldotz on 2007-02-28
i didn't want to use the gnome-network manager, i wanted wifi-radar to take control over wireless.

i'll try those # though. hopefully it adds the functionality i need, thanks for the help.

---

### Post by 900i on 2007-02-28
Uninstall network-manager with Synaptic

---

### Post by havedampton on 2007-03-03
hey,

I also have the broadcom 4311 and haven't had any luck getting it to work, or even finding anything about this particular device.

I've spent a good deal of time getting everything else working and this is the ONLY thing standing in my way.  I'm a super-beginner so I would need pretty detailed intructions- any help would be GREATLY appreciated. 

Thanks.

---


---
title: "Slow boot, help!"
date: 2007-06-27
forum: General Help
---

### Post by smartboyathome on 2007-06-27
Ok, I am running an up-to-date ubuntu feisty install. I restarted today and noticed that, after I log into grub, ubuntu loads GNOME, Metacity, and Nautilus (with the desktop) and then stops and takes a couple of minutes before the session manager kicks in, and then everything else starts up at once. Would someone help me?

---

### Post by smartboyathome on 2007-06-27
Anyone? I would really like for this to be solved!

---

### Post by speaker219 on 2007-06-28
My friend's cousin's dad's uncle had the same problem...so...bump!

---

### Post by smartboyathome on 2007-06-29
I got a snapshot of my system booting using bootchart. It shows a apporximately minute long pause before proceding. I cannot tell what is pausing though, perhaps someone else can help?

---

### Post by Ayuthia on 2007-06-29
It looks like it is slowing down while it is configuring networks.  Another way to verify where it is slowing down, is to take out the slash and quiet when booting (it is in /boot/grub/menu.lst and look at the kernel line).

What might help is if you don't have anything configured in /etc/network/interfaces, you can comment out the network cards listed and only leave the lo listing.  For example eth0 and eth1 are commented out:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

---

### Post by smartboyathome on 2007-06-29
Unfortunately, I do need the internet connections (I am constantly connected to it) but I don't think I need dhcp (I don't run a server). Also, would this help raise my boot time from GDM to Desktop and apps loading?

---

### Post by speaker219 on 2007-06-29
Looks like it did have something to do with the network. =P

---


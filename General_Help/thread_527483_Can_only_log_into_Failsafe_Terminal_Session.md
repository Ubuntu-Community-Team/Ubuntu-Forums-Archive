---
title: "Can only log into Failsafe Terminal Session"
date: 2007-08-16
forum: General Help
---

### Post by DragonerDriftr on 2007-08-16
Hello All,
I was messing around with my /etc/network/interfaces file, but after removing my changes and shutting down, when I came back later I found I could not log into anything but an Xterm session. When I try to login to anything else, I am treated to a screen that has a white box in the corner that, when moused over, shifts the cursor to text-entry. Nothing is interactive, nor does the default splash or sound play.

Using 7.04 on an Inspiron E1505 Laptop with a Core Duo chip and ATI graphics
 
Any suggestions?

---

### Post by ddrichardson on 2007-08-16
Post /etc/network/interfaces, minus ip addresses ofcourse (except 0.0.0.0 and 127.0.0.1). I'd imagine there's been a hostname change configured incorrectly - that'll prevent a lot of things working.

---

### Post by jamvegan on 2007-08-16
Perhaps you inadvertently eliminated or modified the loopback configuration.  In Linux, a lot of things that you might not think are network services actually are, via the loopback device.  The default configuration in /etc/network/interfaces is:

> auto lo
iface lo inet loopback

---

### Post by ddrichardson on 2007-08-16
Sorry I was talking rubbish - reading another post about hosts. Anyway jamvegan is right - its most likely the loopback device.

---

### Post by DragonerDriftr on 2007-08-16
Hmm...interesting, as my interfaces file is:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```



::EDIT::

I tried restarting the network using sudo /etc/init.d/networking restart, got a message about duplicate devices, so I removed all the ethx devices, and it seems to be doing fine now. Most interesting...

---

### Post by jamvegan on 2007-08-16
Hm...I see that last month someone else [described exactly the same problem]("http://ubuntuforums.org/showthread.php?p=2994133"), and they thought that it was a permissions problem.  Is it possible that you somehow changed the permissions on your file (perhaps by copying it)?  The default permissions are:
> -rw-r----- 1 root admin 32 2007-08-04 19:41 /etc/network/interfaces

---


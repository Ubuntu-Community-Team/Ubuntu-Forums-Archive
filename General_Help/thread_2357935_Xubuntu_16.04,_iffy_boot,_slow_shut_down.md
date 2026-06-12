---
title: "Xubuntu 16.04, iffy boot, slow shut down"
date: 2017-04-07
forum: General Help
---

### Post by mathog on 2017-04-07
The file /etc/NetworkManager/NetworkManager.conf

contains:

```
[ifupdown]
managed=false
```

and the system only boots to a text console, that is, this was done:

```
sudo systemctl set-default multi-user.target
```

and yet...

On some (only some) startups it still tries to start the network manager, fails, and it locks up.  The console shows messages down
to the "Give root password for maintenance (or type Control-D to continue)", but the keyboard (USB) does not respond.  Sometimes the machine will shutdown then by holding the power button.  Other times a hard reset is necessary.  Reboot to recovery mode and it checks the disk, then do a normal restart and it usually comes back up.


On a "shutdown" or "reboot" it hangs for 90s at:

```
a stop job is running for Raise network interfaces (<time counter here>/1 min 32s)

```

The thing is, this machine has a single, static ethernet. /etc/network/interfaces contains:

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
network xxx.xxx.xx.0
broadcast xxx.xxx.xx.255
gateway xxx.xxx.xxx.254
dns-nameserver xxx.xxx.yyy.zzz xxx.xxx.www.vvv xxx.xxx.uuu.tttt

```

It doesn't need to wait for anything to bring that interface up, no dhcp time out, no wifi, nothing.
It should just pop right up, and shut right down.

Any idea what is wrong here???

---

### Post by Bucky Ball on 2017-04-07
Xubuntu-core 16.04. This is my  /etc/network/interfaces.

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

I have the static setup in Network Manager and perhaps you should try the same.

If you have Network Manager installed, use that. Making changes in  /etc/network/interfaces will confuse it. If you need help setting up the static IP using Network Manager let us know. You could copy my  /etc/network/interfaces file contents directly into yours. 

Also, are you sure the router is not trying to serve an IP in the same range you are trying to set your static IP? That can also cause confusion.

---

### Post by mathog on 2017-04-07
> **Bucky Ball said:**
> I have the static setup in Network Manager and perhaps you should try the same.

Instead I removed network manager.  So far no problems on several reboots.  Perhaps cured, hard to say since it was intermittent.

Now it does this on shutdown:

```
[OK] Stopped target Network
Stopping Raise network interfaces...
(many more lines)
[OK]Deactivated swap /dev/disk/by-label/swap
(wait here for 90s, no countdown shown)
[OK] Stopped raise network interfaces

```

I think that is this bug in systemd:

[https://github.com/systemd/systemd/issues/1615](https://github.com/systemd/systemd/issues/1615)

---


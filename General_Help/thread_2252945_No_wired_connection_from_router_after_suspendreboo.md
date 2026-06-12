---
title: "No wired connection from router after suspend/reboot/reconnect"
date: 2014-11-16
forum: General Help
---

### Post by childintime on 2014-11-16
So up until recently my 5 year old Linksys WRT54GL router was working fine, but for a few days now everytime I wake up Ubuntu from suspend I have no wired internet (wireless devices still have internet), and the only way to fix it is to turn off and turn on the router.
If I don't do that I can't even access administrator page at 192.168.1.1.
It's the same if I disconnect ethernet cable and plug it in again to laptop, I won't have internet unless reboot router once again.

---

### Post by childintime on 2014-11-17
Bump

---

### Post by childintime on 2014-11-19
[COLOR=#333333]So I checked my /etc/network/interfaces:[/COLOR]

```
[COLOR=#333333]
auto lo
iface lo inet loopback[/COLOR]
```
[COLOR=#333333]It looks like this, but not sure if it was always this way. Anyways I changed it into:[/COLOR]

```
[COLOR=#333333]
auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp[/COLOR]
```
[COLOR=#333333]Rebooted, and now it works! Even replugged ethernet cable and it connects automatically. Now sure why is it, because I didn't change anything before, but at least it works.[/COLOR]

---


---
title: "Scan for hosts in subnet"
date: 2008-06-22
forum: General Help
---

### Post by lfaraone on 2008-06-22
Hey, I need a utility to tell me all the IP addresses of hosts in my network. How hard is that?

---

### Post by lisati on 2008-06-22
My router's admin page has an option to display attached devices, and gives i.p. addresses & host names. Or maybe that's not quite what you had in mind.

---

### Post by lfaraone on 2008-06-22
> **lisati said:**
> My router's admin page has an option to display attached devices, and gives i.p. addresses & host names. Or maybe that's not quite what you had in mind.
Hrm... on my router, it'll only display ones that got an address via DHCP...

---

### Post by ddales on 2008-06-22
man arp

---

### Post by lfaraone on 2008-06-22
Turns out the utility I wanted was "ZenMap"

(mini-howto follows)

From another computer:

[LIST=1]
[*]```
sudo aptitude install zenmap
```
[*]```
sudo zenmap &
```
[*]Set "command" to ```
nmap -T Aggressive -A -v <target>
```
[*]Set "Target" to 192.168.1.* (or whatever range your network uses
[*]Click scan and sit back and relax!
[/LIST]

---

### Post by caljohnsmith on 2008-06-22
> **ffm said:**
> Turns out the utility I wanted was "ZenMap"

(mini-howto follows)

From another computer:

[LIST=1]
[*]```
sudo aptitude install zenmap
```
[*]```
sudo zenmap &
```
[*]Set "command" to ```
nmap -T Aggressive -A -v <target>
```
[*]Set "Target" to 192.168.1.* (or whatever range your network uses
[*]Click scan and sit back and relax!
[/LIST]
Using the options with nmap as you give can result in a long time to scan. If you merely want to see if there are any hosts "alive" on your LAN, it would be much better to do a simple ARP + ping scan:
nmap -PR -sP 192.168.1.0/24

---


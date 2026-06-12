---
title: "Iptables and ports"
date: 2006-10-20
forum: General Help
---

### Post by penguinchrissy on 2006-10-20
Ubuntu does NOT leave a system "wide open by default"

As a matter of fact, Ubuntu has a "no open ports" policy by default. If you don't believe me, try running this on a fresh install of Ubuntu 5.10 (Breezy Badger Release):
nmap -sV -O

If you notice, nmap will tell you that 0 ports are open.

The reason Ubuntu doesn't ship with a firewall is because 0 ports are open. Saying it is leaving the system open to attack is analogous to saying that an unlocked steel door welded shut is a security hazard. It isn't! Firestarter is a great iptables frontend, but please don't spread disinformation.

This is something I read on another website and I assume its true becuse many people said the same thing. So I was wondering could this be one of the reasons azureus says that my port is blocked even though I know I have changed my router settings?

---

### Post by ReaderRat on 2006-10-20
Ubuntu does install with a firewall (iptables(. If you want a GUI to work with (easiest), install firestarter:
```
sudo aptitude update
```
Enter your pass word. And then:
```
sudo aptitude install firestarter
```

---


---
title: "Firewall that blocks applications/ports"
date: 2008-04-22
forum: General Help
---

### Post by enneth on 2008-04-22
I have googled and googled for quite some time now, and I cannot seem to find a firewall that is able to do what I want it to.
I have a PG-list of IP-ranges that I want blocked, so they cannot access an application or port (PeerGuardian list). Firestarter does not seem to be able to do this and nor have I had success with moblock. These two just block everything on the entire computer.

So I basically want to be able to load the file with the banned ip-ranges and make it block these on specific applications or ports.

Does anyone know a firewall that is able to do this? Or another way of doing it?

Edit: I found an application called iplist and it seems to do the trick so far. Anyway, please make suggestions on how to do this another way.

---

### Post by wishful9 on 2008-04-22
I found moblock but couldn't get it working and i don't know if it imports pg lists.  sorry if this isn't of any help.

---

### Post by noswal on 2008-04-22
FWIW I have firestarter with inbound policy set to only allow my pc and the  2 other pc's on my network. 192.168.1.0 ...1.1 and ...1.2 and allow ports for samba 137-139 445. The firewall gets lots of inbound hits in the events log but all incoming is blocked and stealthed per grc

---

### Post by wishful9 on 2008-05-22
a blanket block will not work, either you will not get a decent download speed or outgoing connections will connect to the nasty riaa, mpaa or their minions.  some torrent clients will incorporate peerguardians list, i may be completely wrong but i think azureus does.

---

### Post by jre on 2008-05-23
MoBlock (and IPBlock) work both out of the box. For MoBlock just use the repositoy from moblock-deb.sourceforge.net. There's also an GUI available: mobloquer.
MoBlock will start automatically at system boot and use some preconfigured blocklists (basically the same like PeerGuardian).
You just have to make sure that MoBlock is started after other firewall applications as firestarter.

---


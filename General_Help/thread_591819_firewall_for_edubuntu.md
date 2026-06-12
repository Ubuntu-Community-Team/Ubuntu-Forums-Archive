---
title: "firewall for edubuntu"
date: 2007-10-25
forum: General Help
---

### Post by scuba_suit on 2007-10-25
just got edubuntu up and running, how do i get a firewall up?

---

### Post by jshurst on 2007-10-25
Open a terminal and type "sudo aptitude install firestarter", then you can find it under System->Administration->Firestarter

Basically this is a window into iptables and by default ubuntu doesn't open ports, but I like being able to visually see this via Firestarter.

BTW, I've never used Edubuntu, but I looked at the screenshots and it looks like it uses Gnome and I assume it uses the same repositories that Ubuntu uses...so you should be good.

J

---

### Post by por100pre1 on 2007-10-25
Yes, Firestarter will do. Just keep in mind that is unnecessary to keep it running; just open it, configure it, and close it. IPTables will protect your system.

---


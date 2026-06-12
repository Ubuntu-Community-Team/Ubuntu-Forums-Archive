---
title: "Port Forwarding~Azureus~Charter internet"
date: 2007-03-19
forum: General Help
---

### Post by xptweakerntn on 2007-03-19
I recently switched to charter cable from bellsouth dsl, and in the process, we bought a linksys router. somewhere along the process, by port blocking, or our firewall, my azureus and bittorrent and gtk-gnutella, and amule have stopped working. the only one i really want to work is azureus. i have tried port forwarding in my router, but i don't know what port to use, and also not sure about the ip address. it has "192.168.1" already entered, and the you can enter 3 digits afterword. i entered "1", but was wondering if i should put another 2 digits? what ports should i forward, and what should i select in azureus? the same port i forward? i have tried using tutorials, but none of them work very well. actually noone of them have helped me at all. help is apreciated, i am using ubuntu edgy, and charter internet. any more information i can give to help?

---

### Post by H3g3m0n on 2007-03-19
192.168.1.1 sounds right, just make sure its your ip address in ifconfig, or network-manager

The port for Azureus can be changed in the options, it is highly recommended that you do this as some ISPs block or slow the BitTorrent port which means you get slower downloads (even if your ISP doesn't, other peoples do). Choose a higer number like 41234 or something random and just forward that.

The Azureus wiki is a good source of information: [http://www.azureuswiki.com/](http://www.azureuswiki.com/)

---


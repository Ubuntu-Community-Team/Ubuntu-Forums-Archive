---
title: "Program for fair bandwidth distribution across LAN?"
date: 2008-01-23
forum: General Help
---

### Post by enbuyukfener on 2008-01-23
I'm trying to find a program that is installed on all computers on the LAN and it shares information on bandwidth utilisation. The program calculates the number of computers "fighting" for bandwidth and limits the bandwidth accordingly.

e.g.
Total bandwidth capacity: 100KBps
Computer 1: 10KBps
Computer 2: 70KBps
Computer 3: 20KBps

The software notices utilisation is at or near capacity so it gradually reduces C2's usage from 70 until the load is balanced or until there is free bandwidth (e.g. if C3 was downloading at 20KBps but was not limited from his side).

While I usually find what I'm looking for or end up coding it myself, I am stuck here and I feel it will be too much effort to code. Probably because those that have run into this issue have just gone ahead and bought a router that does this on that level or have not bothered. Note my router is a DI-624 so solutions such as DD-WRT won't work due to incompatibility.

---

### Post by erichmj on 2008-01-23
These monitor bandwidth usage. 'sudo apt-get' on any of these names.

bmon
bwbar
bwm
bwm-ng
iftop
iperf
ipfm
cbm
ibmonitor
pktstat
mactrack
MRTG
Cacti


I would also like to point out that what you are asking for is **exactly what your router is for.** Your router model supports QOS(quality of service) filtering. It throttles bandwidth based on a scale of importance you set for different types of services. This allows you to ensure that at any given time, whenever a service must have bandwidth it does. It should be enabled on your router by default, and a little fine tuning is all that is usually required. If it isn't enabled then you should enable it.

If you need help with QOS there are many sites that can be found with google.

---


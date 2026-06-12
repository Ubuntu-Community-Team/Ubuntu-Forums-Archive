---
title: "Log files flooded with &quot;IPVS: Creating netns size=xx id =yy entries !!!"
date: 2017-02-11
forum: General Help
---

### Post by sundeepgoel on 2017-02-11
My kern.log and syslog are flooded with entries like

kernel: [36771.510090] IPVS: Creating netns size=2192 id=1750
kernel: [36771.768022] IPVS: Creating netns size=2192 id=1751
kernel: [36776.757300] IPVS: Creating netns size=2192 id=1752
kernel: [36776.983649] IPVS: Creating netns size=2192 id=1753
kernel: [36780.720768] IPVS: Creating netns size=2192 id=1754
kernel: [36780.987374] IPVS: Creating netns size=2192 id=1755
kernel: [36785.843055] IPVS: Creating netns size=2192 id=1756
kernel: [36786.071057] IPVS: Creating netns size=2192 id=1757

Tried finding a solution on the web / forum search, but no avail !!! 

Please help with :-
1. Which module do these entries belong to ?
2. Which config file controls them?
3. How can these be reduced / stopped e.g. by reducing logging level ?

---


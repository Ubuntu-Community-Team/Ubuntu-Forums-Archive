---
title: "resume causes networking to fail"
date: 2008-04-27
forum: General Help
---

### Post by low profile on 2008-04-27
Here goes with my first post.

Suspend and Resume works great on 8.04 (unlike earlier releases, which would suspend but not resume for me).

Now the problem is that on resume my internet connection does not work.
I use a cable modem attached to a network card.

Before suspend, netstat -i shows eth0 and lo, and afterwards eth1 or eth2,
(both shown below)

Before suspend:-
[SIZE="1"]$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0     12741      0      0 0         10321      0      0      0 BMRU
lo        16436 0      2639      0      0 0          2639      0      0      0 LRU

After resume:-
$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth1       1500 0         4      0      0 0             5      0      0      0 BMRU
lo        16436 0      2656      0      0 0          2656      0      0      0 LRU
$ 

What can I do to correct this?

---


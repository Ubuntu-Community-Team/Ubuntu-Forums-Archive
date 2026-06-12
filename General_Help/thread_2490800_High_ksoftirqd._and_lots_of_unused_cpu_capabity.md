---
title: "High ksoftirqd. and lots of unused cpu capabity"
date: 2023-09-16
forum: General Help
---

### Post by Andrew_Welham on 2023-09-16
Dear All,
I have an ubuntu linux 22.04 server running as a router with iptables running.It works fine.

Whenever i try to push 1Gb per sec though it  get high ksoftirqd, but it seems locked to a single vCPU for each ksoftirqd.
Which given the load is expected.

I have irqbalance running and all the 12 cores of the vm are loaded with irq traffic but not evenly,

Here is part of  top when a transfer is running
   22 root      20   0       0      0      0 R  98.7   0.0   3:58.84 ksoftirqd/1
    40 root      20   0       0      0      0 R  73.8   0.0   7:32.86 ksoftirqd/4

There is plenty of unused capacity on the server and the network is capable of 2.5gb

My question is what can be done to use more the the cpu / network capability, so thinking things  like ksoftyirqd running across multiple cores, so can use more that 100%

Kind Regards
Andrew

---

### Post by Andrew_Welham on 2023-09-16
Narrowed it down a bit it appears to be rules in iptables

---

### Post by MAFoElffen on 2023-09-17
So this issue is resolved? If so, for the benefit of others that may read this later, please explain what happened, and what you did to solve it... That would help others who find this thread in a search on their similar problems..

Please use the Thread Tools in the upper right to mark this as "Solved."

---


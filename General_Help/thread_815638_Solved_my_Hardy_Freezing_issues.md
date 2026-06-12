---
title: "Solved my Hardy Freezing issues"
date: 2008-06-01
forum: General Help
---

### Post by empty_spaces on 2008-06-01
Hopefully, this may help some people having freezing issues with Hardy.
I've seen a lot of threads on the Hardy freezing issue, and I've been having the same problems ever since I upgraded from Gutsy.
My kernel is 2.6.24-17-generic and Hardy would freeze everytime while booting up. After a hard reset, hardy would load up and work fine until the next time I shut down the system and restarted it. Then it would freeze again.
The following bug thread helped resolve my issue. The solution is mentioned towards the bottom half of the thread.

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/200142](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/200142)

I installed the linux-backports-modules for my kernel via synaptic and have not had any freezes since.

Cheers.

---


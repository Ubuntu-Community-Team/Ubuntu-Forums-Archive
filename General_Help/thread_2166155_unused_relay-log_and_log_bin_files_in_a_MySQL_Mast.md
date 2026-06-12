---
title: "unused relay-log and log_bin files in a MySQL Master-Slave replication"
date: 2013-08-08
forum: General Help
---

### Post by ZaHACKieL on 2013-08-08
Hi. I have a Master server with three slaves running Ubuntu 12.04 and one with 10.04, replicating two databases. I just noticed in the my.cnf file of the slaves, that the lines referring to relay-log and log_bin are commented. I've seen in replication tutorials that they always say to use those lines for the replication to work.

In my case, I'm not using those files and the replication is working fine. Should I use them? What are they for?

Thanx!

---


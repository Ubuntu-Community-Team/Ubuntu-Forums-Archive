---
title: "Problem with sysctl change not taking effect"
date: 2014-10-02
forum: General Help
---

### Post by strtwtsn on 2014-10-02
Hi

We're getting an error during a Postgres install and it looks like the fix is to change the kernel.shmmax and  kernel.shmmal


I've tried

sudo sysctl -w kernel.shmmax=4294967296
sudo sysctl -w kernel.shmmal=1048576

sudo sysctl -p to reload the settings


I've also tried putting the changes in /etc/sysctl.conf and restarting as well as in /etc/sysctl.conf.d/30-postgresql-shm.conf and restarting, but each time its kept the old figure.

I've checked all other files in /etc/sysctl.conf.d and entries in /etc/sysctl.conf but no other settings exist for these entries.

What am I doing wrong?

---


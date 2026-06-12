---
title: "How to set auto update the package at night?"
date: 2008-05-13
forum: General Help
---

### Post by hosammy on 2008-05-13
I am using Hardy 8.04 LTS. May I know how to set up to let the system automatically update various packages at night?
I understand the usual practice is the apt-get or the synaptic.
:popcorn:

---

### Post by dcstar on 2008-05-13
> **hosammy said:**
> I am using Hardy 8.04 LTS. May I know how to set up to let the system automatically update various packages at night?
I understand the usual practice is the apt-get or the synaptic.


This is on my 7.10 system, it may well apply to 8.04:

AFAIK you can set the interval in Synaptic-Settings-Repositories-Updates, but the actual time can't be set there.

The apt update is in the /etc/cron.daily folder, so it should be kicked off whenever that all runs (midnight or next reboot afterwards, IIRC)

The file /var/lib/apt/periodic/update-stamp has a time stamp from the previous run, so if you leave your system on you can see when it was run.

---

### Post by housam on 2008-05-13
system >> admin.>> software sources >> updates . then select the daily updates and check for download all updates in the background. and whenever you start your machine at night it will do the job.

---


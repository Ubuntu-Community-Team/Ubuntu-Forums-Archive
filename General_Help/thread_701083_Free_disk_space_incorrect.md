---
title: "Free disk space incorrect"
date: 2008-02-19
forum: General Help
---

### Post by timas on 2008-02-19
Hello, I'm having issues with my drive getting full.. but not really full.

Here's the output from df;
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.0G  4.7G     0 100% /
varrun                 48M   60K   48M   1% /var/run
varlock                48M     0   48M   0% /var/lock
udev                   48M   20K   48M   1% /dev
devshm                 48M     0   48M   0% /dev/shm

Note the total size of 5gb for sda1, then the used of 4.7gb.. that should leave me with .3gb!

Anyone have any idea how I can get those 300megs back into use?

---


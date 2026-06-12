---
title: "Netstat shows connection after dropbox has been removed."
date: 2017-03-29
forum: General Help
---

### Post by RadarG on 2017-03-29
I had drop box installed on my ubuntu server. I removed it after awhile. When I do a netstat I see the following. This is surviving reboots.

ubunutu:~$ sudo apt-get purge nautilus-dropbox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'nautilus-dropbox' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

tcp        0      0 192.168.0.190:54544     client.v.dropbox.:https ESTABLISHED

tcp        0      0 192.168.0.190:54550     client.v.dropbox.:https ESTABLISHED

d.v.dropbox:https CLOSE_WAIT

---

### Post by papibe on 2017-03-29
Hi RadarG.

The software is no longer on the disk, but the service might still loaded in memory.

Try finding it with ps, top, or htop and kill it. That should do it.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by howefield on 2017-03-30
What does..

```
apt-cache policy dropbox
```

give you..

```
sudo apt purge dropbox
```

---


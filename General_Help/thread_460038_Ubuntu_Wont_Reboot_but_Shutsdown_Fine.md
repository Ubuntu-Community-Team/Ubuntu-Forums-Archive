---
title: "Ubuntu Wont Reboot but Shutsdown Fine"
date: 2007-05-31
forum: General Help
---

### Post by CarlosinFL on 2007-05-31
I have a Ubuntu 7.04 machine on my desktop running RAID1 

```
cwilliams@cwilliams:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              229G  3.4G  214G   2% /
varrun               1013M  256K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb           1013M  180K 1013M   1% /proc/bus/usb
udev                 1013M  180K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   33M  980M   4% /lib/modules/2.6.20-15-generic/volatile

```

I notice when I tell Ubuntu to reboot from Gnome, it starts to do the normal thing and then I get the nice pretty Ubuntu screen where the orange bar starts to go away as if it's preparing a shutdown and then when the bar is now completely black, it just sits there for ever. No more HDD activity or anything and never reboots.

When I select shutdown - it however does shutdown the machine fine.

Anybody know why my PC is doing this and or how to check Ubuntu?

---

### Post by CarlosinFL on 2007-06-01
Anyone?

---


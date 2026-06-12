---
title: "Questions regarding Ubuntu on USB Hard Drive"
date: 2007-06-01
forum: General Help
---

### Post by sfmadmax on 2007-06-01
Hello all,

I have an Alienware m9700 that allows me to boot usb devices,, so i went out and bought a usb hard drive..  this way I can keep my stripe (raid0) on the 2 internal hard drives, since it used nvidia raid..     So I got the usb drive, installed ubuntu on it.. and it has been running problem free for the last 4 months... 

The question I have .. is when I run ..

df -k or df -h i get the following,


work@seanmobile:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                 1030264        72   1030192   1% /var/run
varlock                1030264         0   1030264   0% /var/lock
procbususb             1030264       120   1030144   1% /proc/bus/usb
udev                   1030264       120   1030144   1% /dev
devshm                 1030264         0   1030264   0% /dev/shm
lrm                    1030264     23660   1006604   3% /lib/modules/2.6.20-16-generic/volatile

work@seanmobile:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun               1007M   72K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
procbususb           1007M  120K 1006M   1% /proc/bus/usb
udev                 1007M  120K 1006M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
lrm                  1007M   24M  984M   3% /lib/modules/2.6.20-16-generic/volatile

I know this has something to do with the fact im running off of my usb port on the hard drive,   Is there a way I can display my disk size correctly,,  ???  Anyone that runs off of USB hard drive have experience with this?

Thanks
Sean

---

### Post by Ek0nomik on 2007-06-04
What isn't displaying correctly?

---

### Post by Faasnat on 2007-06-13
> **Ek0nomik said:**
> What isn't displaying correctly?
I think it's more of a matter of something not displaying.

---


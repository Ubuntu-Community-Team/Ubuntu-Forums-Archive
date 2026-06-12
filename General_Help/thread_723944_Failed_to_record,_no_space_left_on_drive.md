---
title: "Failed to record, no space left on drive"
date: 2008-03-14
forum: General Help
---

### Post by 4dplane on 2008-03-14
Hi, 
I am working with Flash Media Server on Ubuntu. Recently I deleted a 250G hard drive full of .flv files and I have had problems ever since. First the drive was all screwed up so I repartition it. This worked because I can cp files into the mounted drive and it works; but the Flash Media Server sees the drive as being full even though it is not. I have been looking into this question from the Flash Media Server perspective but it could be a Linux/ Ubuntu thing. And Ideas on what the problem could be?  

Here is my df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18398028   2217532  15245920  13% /
varrun                  257996       108    257888   1% /var/run
varlock                 257996         0    257996   0% /var/lock
procbususb              257996       104    257892   1% /proc/bus/usb
udev                    257996       104    257892   1% /dev
devshm                  257996         0    257996   0% /dev/shm
lrm                     257996     33788    224208  14% /lib/modules/2.6.20-15-generic/volatile
/dev/hdb1            241263968    202884 241061084   1% /opt/macromedia/fms/applications/servcam



Thanks,
4dplane

---

### Post by Mustard on 2008-03-14
From the description of the problem so far, the issue seems to lie with the Flash server.  Linux is seeing the space withereas the Flash server is not.  I suppose something more subtle could be happening with the interaction between the two, but my gut feeling would be for the Flash server being the issue.

---

### Post by Mustard on 2008-03-15
How exactly does this Flash Media server work?

---

### Post by R13120(1&lt; on 2008-03-15
i think i am having a similar problem. my disk space was almost full so i deleted my music  and videos off the drive but the properties still read drive full....???

---


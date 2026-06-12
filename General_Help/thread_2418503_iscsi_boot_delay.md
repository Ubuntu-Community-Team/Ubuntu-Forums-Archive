---
title: "iscsi boot delay"
date: 2019-05-07
forum: General Help
---

### Post by gus_zernial on 2019-05-07
I'm using Kubuntu 18.10 open-iscsi initiator with a QNAP iscsi target NAS volume/LUN, and there's a long delay for the Kubuntu host to boot. $ systemd-analyze blame shows 

2min 6.185s open-iscsi.service
1min 33.968s lvm2-monitor.service

Anyone know how to fix this - or where there's a better forum to post this question?

Thx, Gus

---

### Post by TheFu on 2019-05-07
Support for 18.10 ends next month. Best to move to 19.04 to see if this is solved at this point.
Are you using lvm on the iSCSI devices?  Are you using LVM anywhere?

I don't use iscsi, but I use LVM almost everywhere```
.
           344ms lvm2-monitor.service (single SSD)
          3.852s lvm2-activation-net.service (6 spinning HDDs)
           626ms lvm2-monitor.service (SSD and 1 spinning HDD)

```
The other systems don't use systemd.

Is the networking boot and name resolution fast?

If you don't need any of the iSCSI storage to boot, you could change the dependencies so it happens after the GUI comes up.  
[https://askubuntu.com/questions/1083537/how-do-i-properly-install-a-systemd-timer-and-service/1083647#1083647](https://askubuntu.com/questions/1083537/how-do-i-properly-install-a-systemd-timer-and-service/1083647#1083647)

---


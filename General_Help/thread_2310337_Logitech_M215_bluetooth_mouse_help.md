---
title: "Logitech M215 bluetooth mouse help"
date: 2016-01-18
forum: General Help
---

### Post by dietz-brandon-bd on 2016-01-18
I have a logitech M215 bluetooth mouse, and recently it just stopped connecting to its reciever. i cant get it to reconnect. tried logitech website but only helps windows users. stupid haters. any help would be appreciated.

---

### Post by QDR06VV9 on 2016-01-18
Hi [COLOR=#000000]dietz-brandon-bd
There is bug an old one but still around..
Bug: [/COLOR][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1039143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1039143)
There was a work around posted for that bug, maybe it work for you also.
Script is as follows
```
[COLOR=#000000]#!/bin/bash
[/COLOR][COLOR=#000000]while :; do dmesg|grep logitech-djreceiver|tail -1|grep -q -c "failed with error -32" || exit; echo -n `date`" Driver Reload" ; rmmod hid_logitech_dj ; 
modprobe hid_logitech_dj ; dmesg|grep logitech-djreceiver|tail -1 ; sleep 1; done[/COLOR]
```
Run it as root and it will unload and reload the module until the mouse works.
Regards

---


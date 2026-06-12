---
title: "NDiswrapper + Compiz Gutsy Boot delay.."
date: 2007-10-23
forum: General Help
---

### Post by #Reistlehr- on 2007-10-23
I wanted to see if anyone else was having this problem and if i should file a bug report..

I have a broadcom 4310, with ndiswrapper (Only method to get my wireless to work). When i log in, my desktop hangs about 30 seconds before my wallpaper, gnome-panel, or any appears. The mouse is visual, and moveable. 

Here is the dmesg output i think might have something to do with it. 
> 
[   44.963125] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.963140] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.845666] lp: driver loaded but no devices found
[   45.876708] ppdev: user-space parallel port driver
[   46.131045] audit(1193120565.507:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5336 profile="/usr/sbin/cupsd"
[   50.012774] Failure registering capabilities with primary security module.
[   50.918430] Bluetooth: L2CAP ver 2.8
[   50.918434] Bluetooth: L2CAP socket layer initialized
[   50.922296] Bluetooth: RFCOMM socket layer initialized
[   50.922372] Bluetooth: RFCOMM TTY layer initialized
[   50.922375] Bluetooth: RFCOMM ver 1.8
[   86.400244] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.251914] wlan0: no IPv6 routers present
[  155.026492] irq 7: nobody cared (try booting with the "irqpoll" option)


It only happens when Compiz Fusion and ndiswrapper are running together i think so far. Turn one or the other off, and it the env loads quiick.

---

### Post by bobyy on 2007-10-23
Hello ..
Maybe you can try this ..to delay compiz ....you can change the secconds.
Create a startscript via

nano start-compiz

and type:

#!/bin/bash
compiz --replace &
sleep 5
emerald --replace

maybee it will work`s..hopefully.

[http://forlong.blogage.de/](http://forlong.blogage.de/)     it is good.

---

### Post by #Reistlehr- on 2007-10-23
Thanks for the reply. I'll give it a try.

---


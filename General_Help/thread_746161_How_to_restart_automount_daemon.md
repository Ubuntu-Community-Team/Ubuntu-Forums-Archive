---
title: "How to restart automount daemon?"
date: 2008-04-05
forum: General Help
---

### Post by descentspb on 2008-04-05
When i hotplug usb storage devices, nothing happens and i should mount them manually. I cannot reboot the computer, to check if it will help. What can i do to make it work? Maybe restart some daemon or gnome or something?

---

### Post by warp99 on 2008-04-05
Plug you device in, then run this command:

```
dmesg |tail 
```

this will let us know if the device is being seen. Please post the results here.

---

### Post by descentspb on 2008-04-06
Done that. The output looks so:
```
[ 5587.153045] sd 16:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 5587.153047] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[ 5587.153051]  sdc: sdc1 < sdc5 sdc6 sdc7 >
[ 5587.155877] sd 16:0:0:0: [sdc] Attached SCSI disk
[ 5587.155912] sd 16:0:0:0: Attached scsi generic sg3 type 0
[13686.640939] usb 7-2: USB disconnect, address 3
[43840.460679] usb 7-2: new high speed USB device using ehci_hcd and address 6
[43840.592971] usb 7-2: configuration #1 chosen from 1 choice
[43840.593039] hub 7-2:1.0: USB hub found
[43840.593147] hub 7-2:1.0: 4 ports detected

```

Nevertheless, I'm absolutely sure that the system sees every device. I figured out that the problem is definitely with the HAL daemon. When i booted up, it said "HAL daemon failed to start". It happens every bootup.
Then I started HAL from /etc/init.d and restarted Gnome. The usb hotplug was still not working, though i've seen no hal errors. I went to init 1, started dbus and hal from /etc/init.d, went back to init 2 and **it started working**. :)
But i cannot do that every time, and i would like to figure out other ways of solving the problem, without rebooting, or goin' to init 1.

---

### Post by warp99 on 2008-04-06
We can restart the daemon in the boot sequence a little later in order to make sure it's loaded. Try the following:

```
cd /etc/init.d && sudo gedit hal-restart
```

put the following script in the file:

```
#! /bin/bash

/etc/init.d/hal restart
sleep 2

```

save the file then make it executable:

```
sudo chmod +x hal-restart
```

and finally:

```
cd /etc/rcS.d && sudo ln -s ../init.d/hal-restart S60hal-restart
```

that should start the hal daemon again before you login to your desktop.

---

### Post by descentspb on 2008-04-06
Thanks, mate, i'll try that!

---

### Post by descentspb on 2008-04-06
Well, now my system freezes when doing "restarting hal deamon", until i press ctrl-alt-del and it continues booting, saying that "hal daemon failed to start, please check that dbus is running". Again "init 1, cd /etc/init.d, ./dbus start, ./hal start" resolves the problem.

---

### Post by warp99 on 2008-04-06
According to the script in /etc/init.d/hal it should have started dbus, but obvious it did not so we'll just add it to the /etc/init.d/hal-restart file:

```
#! /bin/bash

/etc/init.d/dbus restart
sleep2


```

Edit:
No need to add the /etc/init.d/hal restart string, just use the one I corrected.

---

### Post by descentspb on 2008-04-06
It works! Thanks

---

### Post by warp99 on 2008-04-06
I'm glad it worked. For some reason dbus is not loading it's services properly during the boot sequence. It may be that a particular piece of hardware just doesn't want to load dbus at that point in the sequence due to a another service or the hardware is not ready or it needs an extra wait state or any host of problems. If you have more time I would search a little bit to find the problem since the 'fix' I gave you is just a workaround. Maybe others are having a the same problem with similar hardware. If this is the case then the developers should be advised.

---


---
title: "Bluetooth refuse to turn on"
date: 2020-06-14
forum: General Help
---

### Post by dragon528 on 2020-06-14
Hi everyone! New to here and ubuntu as well. Several days ago, the bluetooth work perfectly fine. But until today, it stopped working. 

I have been google around and try numerous method to fix it, but the bluetooth still refuse to enable. Apply the method and reboot, also the same. Bluetooth toggle still stuck at off in the settings.

Can anyone comment on this problem?

My ubuntu  18.04.4 LTS

Edit:

I tried running such command before. Still not avail.
> 
[COLOR=#242729][FONT=Consolas]sudo rmmod btusb 
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sleep 1 
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]sudo modprobe btusb
[/FONT][/COLOR]

> [COLOR=#242729][FONT=Consolas]sudo apt-get install --reinstall bluez[/FONT][/COLOR]

---

### Post by VMC on 2020-06-14
You haven't said what you did.
 Go here and follow the link. Find if it helps:
[https://computingforgeeks.com/connect-to-bluetooth-device-from-linux-terminal/](https://computingforgeeks.com/connect-to-bluetooth-device-from-linux-terminal/)

---

### Post by dragon528 on 2020-06-15
> **VMC said:**
> You haven't said what you did.
 Go here and follow the link. Find if it helps:
[https://computingforgeeks.com/connect-to-bluetooth-device-from-linux-terminal/](https://computingforgeeks.com/connect-to-bluetooth-device-from-linux-terminal/)


Sorry that my question is so vague. The link you provided is also not working. I attached a rfkill image as reference.

---

### Post by VMC on 2020-06-15
Did you follow the link completely? What happens when you execute: ```
**bluetoothctl**
```

---

### Post by ActionParsnip on 2020-06-15
If you restart the Bluetooth service after hibernate, is it OK?
If not, if you unload then reload the Bluetooth kernel module, is it OK?

---

### Post by dragon528 on 2020-06-16
The result is not as same as the link. Here is the result.

---

### Post by dragon528 on 2020-06-16
I already tried to google around and did a service restart but it still not avail.
I'm not quite sure about Bluetooth kernel module. I'm still new to ubuntu.

---

### Post by VMC on 2020-06-16
Did you install per this line:```
sudo apt-get -y install bluetooth bluez bluez-tools rfkill
```

from the text?

---

### Post by dragon528 on 2020-06-16
> **VMC said:**
> Did you install per this line:```
sudo apt-get -y install bluetooth bluez bluez-tools rfkill
```

from the text?

Yea, I already completely follow the step. But it still refuse to turn on. I have restart my laptop as well. 

From my windows 10, I have no issue with the Bluetooth.

---

### Post by VMC on 2020-06-16
Any errors from this output:
```
dmesg|grep -i bluetooth
```
journal might gave more info:
```
journalctl -b|grep -i bluetooth
```

---

### Post by dragon528 on 2020-06-17
> **VMC said:**
> Any errors from this output:
```
dmesg|grep -i bluetooth
```
journal might gave more info:
```
journalctl -b|grep -i bluetooth
```

Here you go.

---

### Post by VMC on 2020-06-17
Copy&paste between CODE tags please. No more pictures.

---

### Post by dragon528 on 2020-06-18
> **VMC said:**
> Copy&paste between CODE tags please. No more pictures.


My apologies. Here you go.

```
liam@liamPC:~$ dmesg | grep -i bluetooth[    2.131404] Bluetooth: Core ver 2.22
[    2.131443] Bluetooth: HCI device and connection manager initialized
[    2.131451] Bluetooth: HCI socket layer initialized
[    2.131457] Bluetooth: L2CAP socket layer initialized
[    2.131464] Bluetooth: SCO socket layer initialized
[    2.738447] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.738450] Bluetooth: BNEP filters: protocol multicast
[    2.738460] Bluetooth: BNEP socket layer initialized
[    4.358471] Bluetooth: hci0: Reading Intel version information failed (-110)
[    4.358530] Bluetooth: hci0: command tx timeout
liam@liamPC:~$ journalctl -b | grep -i bluetooth
Jun 15 11:04:39 liamPC kernel: Bluetooth: Core ver 2.22
Jun 15 11:04:39 liamPC kernel: Bluetooth: HCI device and connection manager initialized
Jun 15 11:04:39 liamPC kernel: Bluetooth: HCI socket layer initialized
Jun 15 11:04:39 liamPC kernel: Bluetooth: L2CAP socket layer initialized
Jun 15 11:04:39 liamPC kernel: Bluetooth: SCO socket layer initialized
Jun 15 11:04:40 liamPC systemd[1]: Starting Bluetooth service...
Jun 15 11:04:40 liamPC bluetoothd[979]: Bluetooth daemon 5.50
Jun 15 11:04:40 liamPC systemd[1]: Started Bluetooth service.
Jun 15 11:04:40 liamPC systemd[1]: Reached target Bluetooth.
Jun 15 11:04:40 liamPC bluetoothd[979]: Starting SDP server
Jun 15 11:04:40 liamPC kernel: Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 15 11:04:40 liamPC kernel: Bluetooth: BNEP filters: protocol multicast
Jun 15 11:04:40 liamPC kernel: Bluetooth: BNEP socket layer initialized
Jun 15 11:04:40 liamPC bluetoothd[979]: Bluetooth management interface 1.14 initialized
Jun 15 11:04:40 liamPC NetworkManager[856]: <info>  [1592190280.4726] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Jun 15 11:04:42 liamPC kernel: Bluetooth: hci0: Reading Intel version information failed (-110)
Jun 15 11:04:42 liamPC kernel: Bluetooth: hci0: command tx timeout
Jun 15 11:05:29 liamPC dbus-daemon[1157]: [session uid=1000 pid=1157] Activating via systemd: service name='org.bluez.obex' unit='dbus-org.bluez.obex.service' requested by ':1.75' (uid=1000 pid=1934 comm="gnome-control-center bluetooth " label="unconfined")
Jun 15 11:05:29 liamPC systemd[1082]: Starting Bluetooth OBEX service...
Jun 15 11:05:29 liamPC systemd[1082]: Started Bluetooth OBEX service.
Jun 15 12:14:19 liamPC sudo[5314]:     liam : TTY=pts/2 ; PWD=/home/liam ; USER=root ; COMMAND=/usr/bin/apt-get -y install bluetooth bluez bluez-tools rfkill
liam@liamPC:~$ ^C
liam@liamPC:~$ 
```

---

### Post by VMC on 2020-06-18
Have you searched this error:```
Bluetooth: hci0: Reading Intel version information failed (-110)
Bluetooth: hci0: command tx timeout
```

Don't know what BT device you have? Here's one bug on the above error:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1591167](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1591167)

---


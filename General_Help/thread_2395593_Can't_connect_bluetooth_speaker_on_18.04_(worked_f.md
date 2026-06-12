---
title: "Can't connect bluetooth speaker on 18.04 (worked fine on 17.10)"
date: 2018-07-04
forum: General Help
---

### Post by themeadows94 on 2018-07-04
I've been trying to connect this speaker, which always worked amazingly on 17.10 (on 2 Thinkpads, T450s and T530). The T450s is on 18.04 now, and I just tried connecting the speaker via bluetoothctl and got a super unhelpful error message:

```
$ bluetoothctl
Agent registered
[bluetooth]# agent on
Agent is already registered
[bluetooth]# scan on
Discovery started
[CHG] Controller 00:1A:7D:DA:71:11 Discovering: yes
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# discoverable on
Changing discoverable on succeeded
[CHG] Controller 00:1A:7D:DA:71:11 Discoverable: yes
[bluetooth]# pairable on
Changing pairable on succeeded
[bluetooth]# devices
Device 88:C6:26:A4:19:A6 UE BOOM 2
Device CF:0F:4D:D1:AD:A8 MX Master 2S
Device B8:69:C2:51:09:44 PHILIPS AEA2700
[bluetooth]# remove 88:C6:26:A4:19:A6 
[DEL] Device 88:C6:26:A4:19:A6 UE BOOM 2
Device has been removed
[NEW] Device 88:C6:26:A4:19:A6 UE BOOM 2
[CHG] Device 88:C6:26:A4:19:A6 TxPower: 4
[CHG] Device 88:C6:26:A4:19:A6 Modalias: bluetooth:v000ApFFFFdFFFF
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110d-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110f-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 00000000-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000cade-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000defa-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000afde-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000ffca-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 RSSI: -36
[bluetooth]# trust 88:C6:26:A4:19:A6
[CHG] Device 88:C6:26:A4:19:A6 Trusted: yes
Changing 88:C6:26:A4:19:A6 trust succeeded
[bluetooth]# pair 88:C6:26:A4:19:A6
Attempting to pair with 88:C6:26:A4:19:A6
[CHG] Device 88:C6:26:A4:19:A6 Connected: yes
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 00000000-deca-fade-deca-deafdecacaff
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 00001101-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:A4:19:A6 ServicesResolved: yes
[CHG] Device 88:C6:26:A4:19:A6 Paired: yes
Pairing successful
[CHG] Device 88:C6:26:A4:19:A6 ServicesResolved: no
[CHG] Device 88:C6:26:A4:19:A6 Connected: no
[bluetooth]# connect 88:C6:26:A4:19:A6
Attempting to connect to 88:C6:26:A4:19:A6
[CHG] Device 88:C6:26:A4:19:A6 Connected: yes
Failed to connect: org.bluez.Error.Failed
[CHG] Device 88:C6:26:A4:19:A6 Connected: no
[CHG] Device 88:C6:26:A4:19:A6 Connected: yes
[CHG] Device 88:C6:26:A4:19:A6 Connected: no

```

I tried updating to a newer version of bluez as suggested here:
[https://askubuntu.com/questions/1036195/bluetooth-doesnt-work-after-resuming-from-sleep-ubuntu-18-04-lts?rq=1](https://askubuntu.com/questions/1036195/bluetooth-doesnt-work-after-resuming-from-sleep-ubuntu-18-04-lts?rq=1)
But the only result seems to be bluetoothctl being a little less verbose. The speaker still doesn't connect.

Any ideas on how I could solve this?

---


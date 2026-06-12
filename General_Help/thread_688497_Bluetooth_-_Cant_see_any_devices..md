---
title: "Bluetooth - Cant see any devices."
date: 2008-02-05
forum: General Help
---

### Post by timmy-mac on 2008-02-05
Hi all..

Thanks for your time/energy/boredom. :-)

I've just got myself a tiny little bluetooth adapter for my Eee. It's a common chipset:
```

tim@eeebuntu:~$ lsusb 
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```

It also seems to be 'working': 
```

tim@eeebuntu:~$ hciconfig 
hci0:   Type: USB
        BD Address: 00:1B:DC:0F:DA:4A ACL MTU: 310:10 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:1953 acl:0 sco:0 events:62 errors:0
        TX bytes:1263 acl:0 sco:0 commands:54 errors:0

tim@eeebuntu:~$ hcitool dev
Devices:
        hci0    00:1B:DC:0F:DA:4A

```

However, it just *will not* find my phone!  I've got two Nokia mobiles here, with the visibility and bluetooth turned on.  They can find and pair with each other just fine.  Yet the laptop can't see them and they can't see it (it is also set to be visible):
```

tim@eeebuntu:~$ hcitool scan
Scanning ...
tim@eeebuntu:~$ hcitool inq
Inquiring ...
tim@eeebuntu:~$ sudo hciconfig hci0 inqmode 0
tim@eeebuntu:~$ 

```
My /etc/bluetooth/rfcomm.conf looks like this (phone's mac determined from the mobile itself):
```

tim@eeebuntu:~$ cat /etc/bluetooth/rfcomm.conf 
#
# RFCOMM configuration file.
#

rfcomm0 {
        # Automatically bind the device at startup
        bind yes;

        # Bluetooth address of the device
        device 00:19:2D:46:84:75;

        # RFCOMM channel for the connection
        channel 1;

        # Description of the connection
        comment "Nokia N73";
}

```
And the output when I try to connect:
```

tim@eeebuntu:~$ sudo rfcomm release 0
Can't release device: No such device
tim@eeebuntu:~$ sudo rfcomm connect 0
Can't connect RFCOMM socket: Host is down

```

So, has anyone got any ideas? I've never used bluetooth before, but I'm sure I'm doing everything correctly.  I've restarted the service a few times etc..  - No joy.

The device's little blue light even stops flashing and goes steady while it is scanning etc. - Yet there is no sign of it being able to communicate with any other device.

Is there a way I can get it to connect to itself or something, to see if that works?

Cheers,

Tim

---

### Post by linuxwizard on 2008-02-05
Look over this 

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by timmy-mac on 2008-02-05
Thanks for the input, linuxwizard.  Is there a particular section that you think I've missed?

I have pasted the output to all of the relevant commands listed there, I think.  It also says that Gutsy should pretty much work 'out of the box'.

So is this problem a strange one then, or are they just no bluetoothwizards around? :-)

Cheers,
T

---

### Post by linuxwizard on 2008-02-05
No nothing in particular. I just thought their maybe something there that would help. Something to try or something you might have forgotten to do.

---

### Post by timmy-mac on 2008-02-05
Always worth double checking... :-)

I've just tested this thing on a Windows box.  It's knackered...  - what luck. :/

Cheers anyway.

T

Ed: in case anyone is concerned, I have had another of these delivered and it works fine.

---


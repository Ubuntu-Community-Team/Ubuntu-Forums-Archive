---
title: "Bluetooth PCMCIA"
date: 2007-01-12
forum: General Help
---

### Post by fac on 2007-01-12
I have been trying for a long time now to get my bluetooth PCMCIA card to function. It is a Sitecom CN-504 card, I know the card is functioning as it is blinking and showing it is ready. But no matter what I do I can't see it. 
When I do a "hcitool dev" command it isn't showing any devices. I have tried installing the "bluez-pcmcia-support" package but that doesn't help either. I know that my PCMCIA port is working as I have a USB card in the other port and it works (and switching them doesn't do anything either just having the bluetooth card inserted).

Is there a file or something that need to be setup, or is there just not support for my card?

Any help appreciated

---

### Post by fac on 2007-02-07
I have searching a bit on the net, and found the following page:

[https://launchpad.net/ubuntu/+source/bluez-utils/+bug/46186](https://launchpad.net/ubuntu/+source/bluez-utils/+bug/46186)

but that didn't help. I get the following messages in my syslog when i insert the card
```
Feb  7 11:27:35 fac-laptop kernel: [17183004.724000] pccard: PCMCIA card inserted into slot 1
Feb  7 11:27:35 fac-laptop kernel: [17183004.724000] pcmcia: registering new device pcmcia1.0
Feb  7 11:27:35 fac-laptop kernel: [17183005.000000] ttyS1: detected caps 00000700 should be 00000100
Feb  7 11:27:35 fac-laptop kernel: [17183005.004000] 1.0: ttyS1 at I/O 0x100 (irq = 3) is a 16C950/954
Feb  7 11:27:36 fac-laptop logger: /lib/udev/bluetooth_serial: setserial or hciattach not executable, cannot start /dev/ttyS1
```

and when i type hcid -n in the terminal i get this error

```
hcid[9561]: Bluetooth HCI daemon
hcid[9561]: Service could not become the primary owner.
hcid[9561]: Unable to get on D-Bus
```

I hope this can give some of you a clue of why it is not working!

---

### Post by jsa13 on 2007-09-07
Easily fixed by...

sudo apt-get install setserial

Then you will see in syslog...

Sep  7 14:56:36 foo NetworkManager: <debug info>^I[1189191396.851071] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1_serial_platform_1'). 
Sep  7 14:56:37 foo hcid[14951]: HCI dev 0 up
Sep  7 14:56:37 foo hcid[14951]: Device hci0 has been added
Sep  7 14:56:37 foo hcid[14951]: Starting security manager 0
Sep  7 14:56:37 foo hcid[14951]: Device hci0 has been activated

And naturally, hciconfig is happy...

hci0:   Type: UART
        BD Address: 00:02:72:B1:9C:DC ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:622 acl:0 sco:0 events:17 errors:0
        TX bytes:579 acl:0 sco:0 commands:16 errors:0
        Features: 0xff 0xff 0x0f 0x00 0x00 0x00 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'foo-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 1.1 (0x1) HCI Rev: 0x110 LMP Ver: 1.1 (0x1) LMP Subver: 0x110
        Manufacturer: Cambridge Silicon Radio (10)

---

### Post by fac on 2007-09-07
Thanks for the help!!

I have bought a new computer since that post. So I do not have the problem any more.

But lets hope it can help some others.

---

### Post by Zta on 2007-09-08
Yes, thanks allot.  It helped me make my CF IOGEAR card working.

---

### Post by andis on 2007-09-15
so much thanks!!!

i spent some 3 days looking for solution, why my cards was not recognized. Thank you so much for your post - it works now :)

---

### Post by kingjotte on 2007-09-25
At first when I installed setserial my bluetooth pcmcia card started working, but after a reboot I can't get it working again.

Any tips?

---


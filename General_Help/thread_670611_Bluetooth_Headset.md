---
title: "Bluetooth Headset"
date: 2008-01-17
forum: General Help
---

### Post by DFlame on 2008-01-17
Hi all, trying to get a Nokia headset to work via bluetooth (hopefully in the end I can use it to skype.

I'm a Gutsy user.

Here are some dumps that might help:

The standard GUI refustes to connect to the headset in pairing mode because "the service is not available"

**hcitool stuff**

Here's my dongle:

> hci0:   Type: USB
        BD Address: 00:0C:76:46:F3:6D ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:3176 acl:12 sco:0 events:89 errors:0
        TX bytes:795 acl:10 sco:0 commands:54 errors:0
        Features: 0xff 0xff 0x0f 0x00 0x00 0x00 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'shader-0'
        Class: 0x08010c
        Service Classes: Capturing
        Device Class: Computer, Laptop
        HCI Ver: 1.1 (0x1) HCI Rev: 0x20d LMP Ver: 1.1 (0x1) LMP Subver: 0x20d
        Manufacturer: Cambridge Silicon Radio (10)


Here's a successful scan for the headset:

> Scanning ...
        00:1C:EF:06:44:06       Nokia BH-209

Here's successful pings of the device:

> gmac@shader:~$ sudo l2ping 00:1C:EF:06:44:06
[sudo] password for gmac:
Ping: 00:1C:EF:06:44:06 from 00:0C:76:46:F3:6D (data size 44) ...
4 bytes from 00:1C:EF:06:44:06 id 0 time 57.82ms
4 bytes from 00:1C:EF:06:44:06 id 1 time 65.50ms
4 bytes from 00:1C:EF:06:44:06 id 2 time 32.57ms
4 bytes from 00:1C:EF:06:44:06 id 3 time 35.55ms
4 bytes from 00:1C:EF:06:44:06 id 4 time 43.56ms
4 bytes from 00:1C:EF:06:44:06 id 5 time 51.55ms
6 sent, 6 received, 0% loss


And finally my conf file:

> #
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # D-Bus PIN helper
        dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        #
        #lm accept,master;
        #
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        #
        #lp hold,sniff;
        #
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption
        #auth enable;
        #encrypt enable;
}

When I try to cc to the device I just get taken back to the prompt with no apparent results. The device remains in pairing mode as if nothing has occurred.

I have "Bluetooth Headset Manager" installed which successfully detects the device. It fails to connect with no error message in the gui.

Pointers? Cheers,

Gareth

---

### Post by DFlame on 2008-01-17
Bump

---

### Post by DFlame on 2008-01-18
Nevermind. Solved by switching to Kubuntu.

Gareth

---


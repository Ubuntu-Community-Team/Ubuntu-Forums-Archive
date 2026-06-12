---
title: "Bluetooth on Xubuntu 14.04"
date: 2015-02-01
forum: General Help
---

### Post by ross4 on 2015-02-01
Hello,
I am running Xubuntu 14.04 LTS on a Toshiba NB200. I want to connect to a blue tooth speaker (iHome iBT16) but I can't get things to work. I know the speaker works as I've successfully paired it with an iPhone and run it through wires to the NB200. I know I have blue tooth on the NB200. lsusb shows (among other things):

       Bus 005 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI  
 And hciconfig gives:
 hci0:	Type: BR/EDR  Bus: USB  
 	BD Address: 00:22:58:FE:CE:08  ACL MTU: 310:10  SCO MTU: 64:8  
 	UP RUNNING PSCAN  
 	RX bytes:1068 acl:0 sco:0 events:55 errors:0  
 	TX bytes:1432 acl:0 sco:0 commands:54 errors:0  
 However, when I run Blueman, although it finds the speaker, I get the messages *Device added successfully, but failed to connect * 
 and  
 *Audio Sink Connection Failed: Stream setup fail**ed*
 

 I have done a lot of searching on blue tooth but find that suggestions/help etc. are often specific to particular distributions and that problems seem to come and go, depending on too many things for me to pin down to come up with a diagnostic strategy. I find the command line examples too cryptic for me but I would be very happy to try these again with a bit of hand holding.

 

 Any suggestions on steps to take?  
 Ross

---

### Post by jeremy31 on 2015-02-01
This usually helps with audio ```
sudo pactl load-module module-bluetooth-discover
```

If not, I will need to see the results from terminal for ```
lspci -nnk | grep -iA2 net
``` and ```
hciconfig --all
```

---

### Post by ross4 on 2015-02-01
For the command: sudo pactl load-module module-bluetooth-discover
the result was:
Failure: Module initialization failed

For
lspci -nnk | grep -iA2 net
the result was:
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7159]
    Kernel driver in use: ath9k
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff60]
    Kernel driver in use: r8169

And for
 hciconfig --all

The result was:
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:22:58:FE:CE:08  ACL MTU: 310:10  SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:555 acl:0 sco:0 events:31 errors:0
    TX bytes:1332 acl:0 sco:0 commands:30 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'xubuntu-0'
    Class: 0x700100
    Service Classes: Object Transfer, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 2.1 (0x4)  Revision: 0x13ee
    LMP Version: 2.1 (0x4)  Subversion: 0x13ee
    Manufacturer: Cambridge Silicon Radio (10)

Does any of this make sense?
Ross

---

### Post by jeremy31 on 2015-02-02
Lets see the full output of ```
lsusb
```

---

### Post by ross4 on 2015-02-02
Here is the output
lsusb
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 005 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jeremy31 on 2015-02-02
Any chance you can find a model number for the wifi/bt combo card?  It is printed on the card but it might be on a sticker on the bottom of the computer.  If it is actually a Cambridge Silicon Radio, I don't see much chance to get it to work

---

### Post by ross4 on 2015-02-02
Here is a hand-transciption of the sticker on the back of the machine:

  	 	 	 	   PA3608U-1BTM
 Contains FCC ID: RYYEYTFXCS
 IC: 4389B-EYTFXCS
 CMII ID: 2007DJ1022
 

 CE 0560  Bluetooth
 

 Contains radio device EYTFXCS
 CCAD07LP034AT5
 0471B/POSTEL/2007
 2015
 2.4FH1

There could be a few errors, especially "l" vs "I" vs "1", in this as the sticker has very small print. However, I think it is correct.
I provide the whole thing as it is a bit difficult to decide what the model is.

---


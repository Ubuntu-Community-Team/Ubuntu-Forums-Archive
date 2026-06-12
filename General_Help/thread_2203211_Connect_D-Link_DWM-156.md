---
title: "Connect D-Link DWM-156"
date: 2014-02-02
forum: General Help
---

### Post by lumaja2 on 2014-02-02
Ubuntu 12.04 LTS

Just acquire  from my service provided a new USB adapter DWM-156.
Connect it into usb but nothing happen and I can't find anywhere on computer.
How to connect this?

---

### Post by varunendra on 2014-02-02
Please unplug the Modem > wait for about 10 seconds > replug it > wait for about 30 seconds, then open a terminal (Ctrl-Alt-T) and run the following commands -
```
lsusb
dmesg | tail -20
```
Post back the output of the above commands here so we can see if it is properly detected and switched to modem mode or not.

Along with the above outputs, please also post back the output of -
```
tar tf /usr/share/usb_modeswitch/configPack.tar.gz | grep 2001
```

---

### Post by Yellow Pasque on 2014-02-02
[http://askubuntu.com/questions/168663/enabling-or-installing-d-link-dwm-156-broadband-modem](http://askubuntu.com/questions/168663/enabling-or-installing-d-link-dwm-156-broadband-modem)

---

### Post by lumaja2 on 2014-02-02
Dongle led always red ```
luis@luis-G41M-Combo:~$ lsusb
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 004: ID 046d:082b Logitech, Inc.
 Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
 Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
 Bus 001 Device 006: ID 2001:a706 D-Link Corp. 
luis@luis-G41M-Combo:~$ dmesg | tail -20 
[ 2224.539728] usb 1-3: USB disconnect, device number 5 
[ 2228.248057] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46370 DPT=137 LEN=58  
[ 2242.358103] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=180.178.127.10 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=65211 DF PROTO=UDP SPT=51413 DPT=53152 LEN=102  
[ 2242.358118] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=180.178.127.10 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=65211 DF PROTO=UDP SPT=51413 DPT=53152 LEN=102  
[ 2249.236024] usb 1-3: new high-speed USB device number 6 using ehci_hcd 
[ 2249.375075] scsi3 : usb-storage 1-3:1.0 
[ 2250.373479] scsi 3:0:0:0: CD-ROM            HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS 
[ 2253.984203] sr1: scsi3-mmc drive: 0x/0x caddy 
[ 2253.984465] sr 3:0:0:0: Attached scsi CD-ROM sr1 
[ 2253.984624] sr 3:0:0:0: Attached scsi generic sg3 type 5 
[ 2258.451593] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42867 DPT=137 LEN=58  
[ 2270.437418] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=99.225.4.222 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=4963 DF PROTO=UDP SPT=51413 DPT=51323 LEN=102  
[ 2270.437432] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=99.225.4.222 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=4963 DF PROTO=UDP SPT=51413 DPT=51323 LEN=102  
[ 2288.654130] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36541 DPT=137 LEN=58  
[ 2292.568348] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=197.80.133.2 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=37266 DF PROTO=TCP SPT=35671 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0  
[ 2292.568365] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=197.80.133.2 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=37266 DF PROTO=TCP SPT=35671 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0  
[ 2312.034366] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=46.73.226.88 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=13932 DF PROTO=UDP SPT=51413 DPT=50335 LEN=66  
[ 2312.034381] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=46.73.226.88 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=13932 DF PROTO=UDP SPT=51413 DPT=50335 LEN=66  
[ 2318.884656] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42326 DPT=137 LEN=58  
[ 2349.082190] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42045 DPT=137 LEN=58  
luis@luis-G41M-Combo:~$ 
luis@luis-G41M-Combo:~$ tar tf /usr/share/usb_modeswitch/configPack.tar.gz | grep 2001
05c6:2001
```

---

### Post by Yellow Pasque on 2014-02-02
^That is unintelligible. Please use [ code ][ /code ] tags...

---

### Post by Bucky Ball on 2014-02-03
> **Temüjin said:**
> ^That is unintelligible. Please use [ code ][ /code ] tags...

^^^
This. You can place them at the beginning and end of the code or click 'Go Advanced' (or Adv. Reply for a new post) and use the # icon.

---

### Post by varunendra on 2014-02-03
Was probably a copy-paste from a text file created in Ubuntu, opened in Windows :P

Trying to make it legible for myself and others..
> **lumaja2 said:**
> Dongle led always red
```
luis@luis-G41M-Combo:~$ lsusb
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 004: ID 046d:082b Logitech, Inc.
 Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
 Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
 Bus 001 Device 006: ID **[COLOR="#FF0000"]2001:a706[/COLOR]** D-Link Corp. 
luis@luis-G41M-Combo:~$ dmesg | tail -20 
[ 2224.539728] usb 1-3: USB disconnect, device number 5 
[ 2228.248057] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46370 DPT=137 LEN=58  
[ 2242.358103] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=180.178.127.10 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=65211 DF PROTO=UDP SPT=51413 DPT=53152 LEN=102  
[ 2242.358118] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=180.178.127.10 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=65211 DF PROTO=UDP SPT=51413 DPT=53152 LEN=102  
[ 2249.236024] usb 1-3: new high-speed USB device number 6 using ehci_hcd 
[ 2249.375075] scsi3 : usb-storage 1-3:1.0 
[ 2250.373479] scsi 3:0:0:0: CD-ROM            HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS 
[ 2253.984203] sr1: scsi3-mmc drive: 0x/0x caddy 
[ 2253.984465] sr 3:0:0:0: Attached scsi CD-ROM sr1 
[ 2253.984624] sr 3:0:0:0: Attached scsi generic sg3 type 5 
[ 2258.451593] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42867 DPT=137 LEN=58  
[ 2270.437418] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=99.225.4.222 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=4963 DF PROTO=UDP SPT=51413 DPT=51323 LEN=102  
[ 2270.437432] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=99.225.4.222 LEN=122 TOS=0x00 PREC=0x00 TTL=64 ID=4963 DF PROTO=UDP SPT=51413 DPT=51323 LEN=102  
[ 2288.654130] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36541 DPT=137 LEN=58  
[ 2292.568348] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=197.80.133.2 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=37266 DF PROTO=TCP SPT=35671 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0  
[ 2292.568365] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=197.80.133.2 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=37266 DF PROTO=TCP SPT=35671 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0  
[ 2312.034366] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=46.73.226.88 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=13932 DF PROTO=UDP SPT=51413 DPT=50335 LEN=66  
[ 2312.034381] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=46.73.226.88 LEN=86 TOS=0x00 PREC=0x00 TTL=64 ID=13932 DF PROTO=UDP SPT=51413 DPT=50335 LEN=66  
[ 2318.884656] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42326 DPT=137 LEN=58  
[ 2349.082190] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00 SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42045 DPT=137 LEN=58  
luis@luis-G41M-Combo:~$ 
luis@luis-G41M-Combo:~$ tar tf /usr/share/usb_modeswitch/configPack.tar.gz | grep 2001
05c6:[COLOR="#FF0000"]2001[/COLOR]
```

..and after having done that, we can clearly see that the device didn't change its mode from Storage device to Modem, which is obvious since the installed usb_modeswitch package is old and doesn't have this device id included.

I don't have packages from Saucy, but from the Raring package, a *similar* id file is 2001:a80b, so we may try the same message content here to try our luck with the currently installed usb_modeswitch version.

@lumaja2,
Please open a terminal and try this command while the USB dongle is plugged in -
```
sudo usb_modeswitch -W -v 0x2001 -p 0xa706 -M ""555342431234567800000000000003f0010100000000000000000000000000"
```
Now copy everything that occurs in the terminal and post back here.

After the above process in terminal finishes, check -
```
lsusb | grep 2001
```
Does it show the same "2001:a706" or a changed ID? If it remains the same, I would assume our blind shot missed the target. We may try again the same command with "-R" option added, but maybe the best thing to do would be to follow the link that Temüjin posted earlier.

**EDIT:**
..or try a Live CD of 13.10 to see if the dongle is natively supported on it.

And if you are indeed copying everything from terminal to a text file, then opening it on Windows, make sure to select the "Line Ending" (at the bottom of the "Save" dialogue of Gedit) as "Windows". This will make the line ending same as in windows, making it appear the same in both windows and Ubuntu.

For using 'Code' tags, please see the link in my signature. :)

---

### Post by lumaja2 on 2014-02-03
Dongle led always red ```
luis@luis-G41M-Combo:~$ lsusb Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 004: ID 046d:082b Logitech, Inc. Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120 Bus 001 Device 006: ID 2001:a706 D-Link Corp. 
``````
luis@luis-G41M-Combo:~$ dmesg | tail -20 [ 2224.539728] usb 1-3: USB disconnect, device number 5 [ 2228.248057] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00^ SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP^ SPT=46370 DPT=137 LEN=58 [ 2242.358103] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=180.178.127.10 LEN=122^ TOS=0x00 PREC=0x00 TTL=64 ID=65211 DF PROTO=UDP SPT=51413 DPT=53152 LEN=102 ^ [ 2242.358118] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=180.178.127.10 LEN=122^ TOS=0x00 PREC=0x00 TTL=64 ID=65211 DF PROTO=UDP SPT=51413 DPT=53152 LEN=102^ [ 2249.236024] usb 1-3: new high-speed USB device number 6 using ehci_hcd [ 2249.375075] scsi3 : usb-storage 1-3:1.0 [ 2250.373479] scsi 3:0:0:0: CD-ROM HSPA USB SCSI CD-ROM 6225 PQ: 0 ANSI: 0 CCS [ 2253.984203] sr1: scsi3-mmc drive: 0x/0x caddy [ 2253.984465] sr 3:0:0:0: Attached scsi CD-ROM sr1 [ 2253.984624] sr 3:0:0:0: Attached scsi generic sg3 type 5 [ 2258.451593] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00^ SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP^ SPT=42867 DPT=137 LEN=58 [ 2270.437418] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=99.225.4.222 LEN=122^ TOS=0x00 PREC=0x00 TTL=64 ID=4963 DF PROTO=UDP SPT=51413 DPT=51323 LEN=102^ [ 2270.437432] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=99.225.4.222 LEN=122^ TOS=0x00 PREC=0x00 TTL=64 ID=4963 DF PROTO=UDP SPT=51413 DPT=51323 LEN=102^ [ 2288.654130] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00^ SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP^ SPT=36541 DPT=137 LEN=58 [ 2292.568348] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=197.80.133.2 LEN=60^ TOS=0x00^ PREC=0x00 TTL=64 ID=37266 DF PROTO=TCP SPT=35671 DPT=80^ WINDOW=14600 RES=0x00 SYN URGP=0 [ 2292.568365] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=197.80.133.2 LEN=60^ TOS=0x00 PREC=0x00 TTL=64 ID=37266 DF PROTO=TCP SPT=35671 DPT=80^ WINDOW=14600 RES=0x00 SYN URGP=0 [ 2312.034366] [UFW AUDIT] IN= OUT=eth0 SRC=10.0.0.3 DST=46.73.226.88 LEN=86^ TOS=0x00^ PREC=0x00 TTL=64 ID=13932 DF PROTO=UDP SPT=51413 DPT=50335 LEN=66 [ 2312.034381] [UFW ALLOW] IN= OUT=eth0 SRC=10.0.0.3 DST=46.73.226.88 LEN=86^ TOS=0x00 PREC=0x00 TTL=64 ID=13932 DF PROTO=UDP SPT=51413 DPT=50335 LEN=66 [ 2318.884656] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00^ SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP^ SPT=42326 DPT=137 LEN=58 [ 2349.082190] [UFW AUDIT] IN=eth0 OUT= MAC=1c:6f:65:43:ac:46:28:c6:8e:91:ac:06:08:00^ SRC=10.0.0.2 DST=10.0.0.3 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP^ SPT=42045 DPT=137 LEN=58 
``````
luis@luis-G41M-Combo:~$ luis@luis-G41M-Combo:~$ tar tf /usr/share/usb_modeswitch/configPack.tar.gz | grep 2001 05c6:2001
``````
 luis@luis-G41M-Combo:~$ In 05c6:2001 2001font colour red.
``` second Terminal result: ```
luis@luis-G41M-Combo:~$ sudo usb_modeswitch -W -v 0x2001 -p 0xa706 -M ""555342431234567800000000000003f00101000000000000 00000000000000" > sudo usb_modeswitch -W -v 0x2001 -p 0xa706 -M ""555342431234567800000000000003f00101000000000000 00000000000000" [sudo] password for luis: Taking all parameters from the command line * usb_modeswitch: handle USB devices with multiple modes * Version 1.2.3 (C) Josua Dietze 2012 * Based on libusb0 (0.1.12 and above) ! PLEASE REPORT NEW CONFIGURATIONS ! DefaultVendor= 0x2001 DefaultProduct= 0xa706 TargetVendor= not set TargetProduct= not set TargetClass= not set TargetProductList="" DetachStorageOnly=0 HuaweiMode=0 SierraMode=0 SonyMode=0 QisdaMode=0 GCTMode=0 KobilMode=0 SequansMode=0 MobileActionMode=0 CiscoMode=0 MessageEndpoint= not set MessageContent="555342431234567800000000000003f001 0100000000000000000000000000 sudo usb_modeswitch -W -v 0x2001 -p 0xa706 -M 555342431234567800000000000003f0010100000000000000 000000000000" NeedResponse=0 ResponseEndpoint= not set InquireDevice enabled (default) Success check disabled System integration mode disabled Error: MessageContent hex string has uneven length. Aborting.
``````
 luis@luis-G41M-Combo:~$ lsusb | grep 2001 Bus 001 Device 007: ID 2001:a706 D-Link Corp. 
```

---

### Post by Bucky Ball on 2014-02-03
*Thread closed.*

You were asked nicely twice and it was explained to you how to use code tags; code tags were added by another user for you and you were advised about how to get the correct formatting if you were posting from Windows. 

To repeat: the above post #8 is unintelligible so perhaps try again, and this time with code tags, in a new thread in ***Networking & Wireless***. You'll greatly improve your chances of getting support. Thanks.

---


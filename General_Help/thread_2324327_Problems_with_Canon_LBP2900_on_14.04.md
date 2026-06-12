---
title: "Problems with Canon LBP2900 on 14.04"
date: 2016-05-12
forum: General Help
---

### Post by thomas108 on 2016-05-12
Hi, hope some one can help

I have been using my LBP2900 printer on ubuntu 14.04 for 2 years without major problems, but recently after some updates it stopped working, im unsure what updates it was as I did not pay much attention to it..

I then tried uninstall and reinstall the printer and follower all the guides I could find.

but problem still the same, it say communication error.. and I have no idea what to do..

** captstatusui -P LBP2900**
 says "communication error"

**sudo ccpdadmin**
says:
CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787


 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP2900     : ccp         : //localhost:59787     : /dev/usb/lp0 : 

[B]lsusb
[/B]says:
Bus 002 Device 004: ID 0b05:7782 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 09da:c10a A4Tech Co., Ltd. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04a9:2676 Canon, Inc. CAPT Device
Bus 001 Device 002: ID 1908:2310 GEMBIRD 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1a2c:2d23 China Resource Semico Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 **/usr/sbin/lpinfo -v**
says
network ipps
network ipp
direct usb://Canon/LBP2900?serial=0000D2D6SIQU
network lpd
network socket
network ipp14
direct ccp
network https
network http
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS4?baud=115200
direct hp
network smb
direct hpfax


hope some one can help me to get this fixed....

---

### Post by thomas108 on 2016-05-14
I updated to 16.04

problem still same, when writing 
ccpdadmin:

&#9679; ccpd.service - LSB: Canon Printer Daemon for CUPS
   Loaded: loaded (/etc/init.d/ccpd; bad; vendor preset: enabled)
   Active: active (running) since Sat 2016-05-14 15:10:05 PHT; 6s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 6427 ExecStop=/etc/init.d/ccpd stop (code=exited, status=0/SUCCESS)
  Process: 6463 ExecStart=/etc/init.d/ccpd start (code=exited, status=0/SUCCESS)
    Tasks: 3 (limit: 512)
   CGroup: /system.slice/ccpd.service
           &#9500;&#9472;6469 /usr/sbin/ccpd
           &#9500;&#9472;6470 /usr/sbin/ccpd
           &#9492;&#9472;6475 captmon2 --data-write-fd=4 --data-read-fd=11 --cmd-write-fd=12 --cmd-read-fd=15 --output-fd=-1 --input-fd=-1


and [B]captstatusui -P LBP2900
says "communication error"[/B]

---

### Post by thomas108 on 2016-05-14
UPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787


 Entry Num  : Spooler	: Backend	: FIFO path		: Device Path 	: Status 
 ----------------------------------------------------------------------------
     [0]    : LBP2900 	: ccp 		: //localhost:59787 	: /dev/usb/lp0 	: Modified


can any come with a clue why it cant work...

---

### Post by pdc on 2016-05-21
I just wondered which version of the CAPT driver you were using: Canon issued a new 2.7 version last December: as you said you had successfully used the CAPT? driver for a couple of years ........ I wondered if the new driver would help; Canon did work to ensure compatibility with 64bit as well as 32bit installs; 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html) 

it comes down as Linux_CAPT_PrinterDriver_V270_uk_EN.tar.gz

I could dig around and find the install instructions if needed: but you have successfully done this in the past: Canon give an excellent how to guide on reinstalling a new driver: including how to delete the old spool registration and then creating a new one

---


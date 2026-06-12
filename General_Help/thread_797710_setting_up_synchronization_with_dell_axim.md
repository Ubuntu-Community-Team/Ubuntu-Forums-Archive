---
title: "setting up synchronization with dell axim"
date: 2008-05-17
forum: General Help
---

### Post by Eklod on 2008-05-17
I am new to Ubuntu 8.*, which I installed on my Dell Inspiron 2200 - I would appreciate advice for setting up connection and synchro through USB with Dell Axim x51 , which is running Windows Mobile 5.0. 

 I thank you in advance for your suggestions.

---

### Post by gwcarpenter on 2008-07-16
I know this is 2 months old but I think it is important to figure this out.

You might want to take  a look into using SynCE and multisync.
search your package manager for these.

First type in these commands in the terminal to see if your axim even shows up.

dmesg

-should show a long list of devices connected.

lsusb

-shows connected and recognized usb devices

cat /proc/bus/usb/devices

-shows anything connected by a usb connection

I have a Dell Axim X51 and heres what I get using cat

T:  Bus=05 Lev=02 Prnt=02 Port=02 Cnt=03 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS=16 #Cfgs=  1
P:  Vendor=413c ProdID=4011 Rev= 0.00
S:  Manufacturer=Dell Inc.
S:  Product=**Dell Axim X51**
S:  SerialNumber=1b133823-0506-2138-2800-0050bfe45ce5
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=rndis_host
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=rndis_host
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

Take note of the Driver field. Newer pocket pcs running in Hardy (8.04) use the rndis driver for serial connections, older pocket pcs use the ipaq driver. I'm still googling around for a way to configure the axim using rndis and synce and multisyce. I'll post back when I have some real answers.

-George

---


---
title: "eth0 gone???"
date: 2005-10-14
forum: General Help
---

### Post by aran384 on 2005-10-14
for some reason since last update ive done my eth0 has just disappered and i now have no internet on my ubuntu computer ?? 


any1 able to help me.... ? 

btw the update was about 2 days that was last one ive done...

---

### Post by z_pod on 2005-10-14
Hi,

some details would be useful.
firstly I would suggest you to apt-get upgrade to the latest release.

assuming eth0 being a built-in ethernet
1. can you post dmesg output ?
2. ifconfig (eth0) output as well
3. is the eth card attached to some device (hub) or connected to a ISDN/ADSL router/modem ? - in which case, as you know the connection must be established before eth0 can be configured. 
4. (sorry, I made this error myself) check cables, power etc...:rolleyes: 

Regards

---

### Post by Cathbard on 2005-10-14
I just installed breezy and my ethernet disappeared too...........well it seemed to at first.
Have you gone to System Tools>Network Tools and configured the ethernet device? Mine was talking out the ethernet loopback, once I selected eth(0) and configured it with dhcp I was up and running.

PS: so far breezy is looking very slick.

---

### Post by aran384 on 2005-10-14
cables are fine cause i got my windows comp plugged into same switch....

it all happened 2 days ago... 

i cant get the info to you because i dont have internet or lan... so :S

---

### Post by aran384 on 2005-10-14
its some kinda pci bus error or summat .... 

am not sure extactly but its something like that....

---

### Post by Ubuntu_User on 2005-10-14
What kind of ethernet card do you have? Is it an RTL8139?

---

### Post by 11hjpphty76lkjj on 2005-10-14
I had the same issue happen when I installed Breezy as well on a HP d325.  I then went back to Hoary and it works fine.  But that was before the release, so apparently whatever the issue was is still there. 

Aaron

---

### Post by gertoft on 2006-09-14
Same thing just happen to me, almost, running Ubuntu Breezy since before the summer.

After restarting my computer as asked to have the latest software updates fully installed all eth devices has dissapered.

Having a HP nx7000.

//Nick

---

### Post by jdong on 2006-09-14
There are related problems with the recent kernel update.

What kind of network card is it? Can you post full lspci output if you're affected?

---

### Post by gertoft on 2006-09-15
I have a Intel PRO/Wireless 2200bg MiniPCI 11g for the wireless part.

I get back when I have rebooted my laptop, to start Ubuntu, to do the lspci.

//Nick

---

### Post by gertoft on 2006-09-15
Here is my lspci:

0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
0000:02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
0000:02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller

How do I get my eth's back?

//Nick

---


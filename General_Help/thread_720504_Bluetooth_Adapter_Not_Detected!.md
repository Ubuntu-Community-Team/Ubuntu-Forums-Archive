---
title: "Bluetooth Adapter Not Detected!"
date: 2008-03-10
forum: General Help
---

### Post by kanigit on 2008-03-10
I finally got everything set up the way I want on my Ubuntu installation and the only thing keeping me from not uninstalling vista is my bluetooth headset. I have an Insignia NS-BTHDST headset that works perfectly in windows but I cant seem to get hcitools to detect the usb adapter for the life of me. I've tried several things without any success. The strange thing is ubuntu detect the adapter when it is plugged using the command lsusb but hcitool does not detect it. I was beginning to think that perhaps the adapter is just not supported for some reason until I found this ([http://www.redhat.com/archives/rhl-list/2007-December/msg04204.html](http://www.redhat.com/archives/rhl-list/2007-December/msg04204.html)) which seems to show the adapter being detected. 

Here is the results of lsusb and hcitool dev before plugging in the adapter:

> 
knight@knight-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
knight@knight-laptop:~$ hcitool dev
Devices:


Here is the results after it's plugged in:

> 
knight@knight-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 012: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 011: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 010: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
knight@knight-laptop:~$ hcitool dev
Devices:


---

### Post by kanigit on 2008-03-10
Well as I kept toying with this thing I decided to run an ubuntu live cd on my desktop and see if the adapter was detected and sure enough it worked perfectly. I ran lsusb and hcitool dev to see its output to compare

> 
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 009: ID 0a5c:2120 Broadcom Corp. 
Bus 004 Device 008: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 007: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:006e Microsoft Corp. MN510 802.11b Adapter
Bus 002 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ hcitool dev
Devices:
        hci0    00:02:76:0C:6E:D0



I noticed the difference is the "Bus 004 Device 009: ID 0a5c:2120 Broadcom Corp."

Its good to know that the adapter does work but why is it not showing up on my laptop?

---

### Post by kanigit on 2008-03-10
New Update:

I ran the same test with the ubuntu live cd on another laptop. My laptop is a Gateway and the other one is a Dell and both have the same problem detecting the bluetooth adapter unlike the desktop. I noticed that lsusb returned the same output on both laptops with onl the 3 broadcom entries and I also noticed that when I run lspci that both laptops use Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI wheres the desktop was a VIA host controller. Can I assume the USB host controller is to blame?

---

### Post by KhanTG on 2008-05-07
I am having the same issue.  I will let you know what I find, unless you have already found the answer.  If you have.. please post it.  Regards

---

### Post by K-Starz on 2008-06-26
I have the same problem -

adapter shows up in lsusb (three entries for broadcom. Kinfocenter shows it is a 'hub', proper speed, etc.

However, I can not get anything from hci-whatever.

I got this headset just to talk to my friend in Australia, anyway, and she thinks the sound quality makes me sound like I have a major lisp. That's on Vista... I really want to try it on linux, anyway, before I return the thing!

---


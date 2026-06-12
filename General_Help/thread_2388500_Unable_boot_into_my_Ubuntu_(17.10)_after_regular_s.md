---
title: "Unable boot into my Ubuntu (17.10) after regular small update"
date: 2018-04-03
forum: General Help
---

### Post by zoe-scutterbug on 2018-04-03
Hi  

 
 
 If anyone can help me fix this I would be naturally very very happy.

 My computer is Zotac MAGNUS EN1070 details below.
 It has two partitions on  separate SSDs.
 On the first is my Ubuntu 17.10 set up which normally runs much smoother and is where most of my preferred set up etc is.
(On the second I have a working, but a bit clunky Mint Partition.)

 
 Before the weekend I did a simple update and now I am unable to boot into my Ubuntu partition from my Grub 2.02~beta3 etc

 
 Instead of taking me to the login screen the boot process stops at …

 
```

 ACPI error [/SB_PC10.XHC_.RHCB.HS11] namespace lookup failure AE-NOT-FOUND (20170531/DSWLOAD-210)
 
```
 Then 3 lines repeating the ACPI exception  AE-NOT-FOUND

 
 last 2 line  ....

 ```


 ACPI error: 1 tableload failure,7 successful (2017o531/ tbxload-246)

 usbhid 1-4:1.2 could not find interupt endpoint

 
```
 then
 Busy Box  & initramfs
 
 
 I have no idea how to proceed ~ apologise I have the computer skills of a rather forgetful Australopithecus…. I banging the rocks together here mostly.

Sorry if I am missing anything obvious.

 
 
 (When I boot into my Mint partition I do get similar ACPI errors but the login screen appears.)

 
 
 
 Zotac MAGNUS EN1070
 CPU: Intel(R) Core(TM) i5-6400T CPU @ 2.20GHz (2200 MHz)

 Memory: 15997 MB

 Graphics Card Vendor: NVIDIA Corporation : GeForce GTX 1070/PCIe/SSE2

 2 x ATA Samsung SSD 850

 
 UBUNTU 17.10: Desktop Mate : Linux 4.13.0-36

Many thanks in advance
Zoe (its late here so might not see replies until tomorrow)

---

### Post by zoe-scutterbug on 2018-04-05
took it to a shop

they said the file system was corrupted (2nd time), that fdisk was not working and that the 8 month old SSD was working at 98%. :(

---


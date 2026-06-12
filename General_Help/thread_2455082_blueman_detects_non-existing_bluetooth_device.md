---
title: "blueman detects non-existing bluetooth device"
date: 2020-12-11
forum: General Help
---

### Post by helen314 on 2020-12-11
I have a bluetooth enabled , with serial to bluetooth dongle, device. 
blueman finds it and pairs with it. 

Then I physically remove the dongle. 

blueman finds it and pairs with it again 

Rebooting Ubuntu (16.04 ) does not solve the problem.

blueman finds it and pairs with non-existing  device again.

Edited

Using "blueman" I can "remove from list" an "active"  bluetooth device - no problem.

I cannot do same , remove from list, with device which is no longer nowhere near my PC - hence not active but
still exists in the list. There is no option to activate or remove it. 


Conclusions 
"blueman" maintains list of ALL bluetooth devices it scanned and found.
It is unknown where such list is physically located. 

**How do I locate such list and gain direct control over it ?**

Since I really do not need  "blueman" , I have my own application , I would prefer to disable it, but ONLY "blueman".
A suggestion was posted to "uninstall "blueZ*" , however I need to keep Linux kernel ( official Bluetooth "blueZ" stack )
Bluetooth operating, only want to get rid of "blueman" application interference with  my application.

---


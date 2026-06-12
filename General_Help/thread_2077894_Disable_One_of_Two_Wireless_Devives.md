---
title: "Disable One of Two Wireless Devives"
date: 2012-10-29
forum: General Help
---

### Post by FeraTech on 2012-10-29
Is there any easy way to disable one of two wireless devices.

The internal wireless of the PC is not very good. So an external USB wireless device was added.

Both happen to be the same chipset. It's a realtek wireless chipset. Don't remember the exact model.

Also, strangely enough the BIOS does not contain any settings to disable the wireless.

I have seen some walkthroughs to disable the driver getting loaded this obviously is not an option since both controllers have the same chipset and driver.

Please tell me there is an easy way to do this.

I have tried setting the MAC address on the wireless network. However, Network Manager decides to recreate the wireless network with a blank MAC address.

Please help.

---

### Post by kanikilu on 2012-11-02
This lists pretty much every way to disable wireless:

[http://www.cyberciti.biz/faq/linux-remove-wireless-networking-wifi-802-11-support-drivers/](http://www.cyberciti.biz/faq/linux-remove-wireless-networking-wifi-802-11-support-drivers/)

Since in your case, you just want to disable a particular adapter, I think what you want would be in the section called "Deactivate Wireless Interfaces (Remove Config Files)". Obviously, only disable the one you want to disable...

---

### Post by p1977p on 2012-11-02
1) install rfkill .
```
$ sudo apt-get install rfkill
```2)type in terminal :
```
$ sudo rfkill list
```This should list the 2 devices (1 in my case):
```
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

``` Note the number 0 or 1 of the specific device you want to disable. My device is already disabled. ( "Soft blocked: yes")

3) type 
```
$ sudo rfkill disable 0
```to disable device 0.
To enable substitute disable with enable.

---

### Post by grahammechanical on 2012-11-02
As regards the BIOS, did you look under USB devices? Also, you may find that the wireless adapter is a USB expansion card that can be physically removed. My motherboard was sold in 2 forms. One model had a wireless adapter. The other model did not. So, the wireless adapter is an expansion card connected to a USB internal port.

Regards.

---


---
title: "wireless help"
date: 2007-01-15
forum: General Help
---

### Post by zoidburg016 on 2007-01-15
Hi I have kubuntu 6.06 and a belkin usb wireless adapter. it recognizes that the wireless card is there and it is activated, but I don't know how to connect with it. Any help?

---

### Post by thomasaaron on 2007-01-16
So, there should be an icon in the upper right corner that looks like a computer monitor.
Right click on it. Select properties. Select WLAN0 and configure.
Does that do it?
If not, what have you tried so far?

---

### Post by thomasaaron on 2007-01-16
I was just thinking. If that does not work, go to a terminal and type:
sudo ifup wlan0

you'll be prompted for a password, then it should connect you. Usually takes about thirty seconds.

---

### Post by zoidburg016 on 2007-01-16
Ok, I fund the thing that lets me chose the thing that scans for available wireless networks then it says 
Radio of your wireless card seems to be turned off using an external switch on your computer.

You need to turn it on to be able to use wireless networks.

---

### Post by zoidburg016 on 2007-01-16
by the way, this wireless card works in windows.

---

### Post by zoidburg016 on 2007-01-16
> **thomasaaron said:**
> I was just thinking. If that does not work, go to a terminal and type:
sudo ifup wlan0

you'll be prompted for a password, then it should connect you. Usually takes about thirty seconds.

I tried that and it said 

ifup: interface wlan0 already configured

---


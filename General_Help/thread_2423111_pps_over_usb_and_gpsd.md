---
title: "pps over usb and gpsd"
date: 2019-07-17
forum: General Help
---

### Post by archi77 on 2019-07-17
Hi,

In order to synchronize two laptops together, I bought 2 gps delivering 1 PPS over usb dongle. (adafruit ultimate usb gps). I arrived to synchronize with the gps easily, but gpsd is not finding any PPS signal. 
The fact is that this gps is sending the PPS signal the the virtual Ring Indicator pin of the serial port. Using Python, I detected the pps signal over this pin. The problem is that, to my mind, GPSD is not checking this pin. 

My first question is "can i make gpsd check this pin drectly"?

Secondly, I started to program a linux module that would read the usb port, check the right pin and create a pps event. My Problem is that I do not know how to read the usb port and especially this pin. creating a pps event is pretty easy, I check Ktimer.c.

Thanks a lot for your help,
Archi

---


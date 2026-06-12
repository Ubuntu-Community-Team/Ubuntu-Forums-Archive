---
title: "Plantronics Headset"
date: 2013-03-09
forum: General Help
---

### Post by Elvis99 on 2013-03-09
Hi all,

I've bought a Plantronics Headset (Gamecom 780) and it somehow is not appearing in the sound settings.

lsusb gives me this

              > Bus 004 Device 002: ID 047f:c010 Plantronics, Inc.                      

     
 

dmesg

                                                         [  428.911373] input: Plantronics Plantronics GameCom 780 as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.3/input/input6
[  428.911680] generic-usb 0003:047F:C010.0005: input,hidraw1: USB HID  v1.00 Device [Plantronics Plantronics GameCom 780] on  usb-0000:00:12.1-2/input3                      

     
 

So it seems, it is recognized by the system but I can't hear anything in the headphones. In the sound settings, the headset isn't even displayed. Can pleaase anyone point me in the right direction to get it working?

Thanks!

---

### Post by Elvis99 on 2013-03-10
I got it to work.
all that was needed was to run

sudo modprobe snd-usb-audio 
:guitar:

---


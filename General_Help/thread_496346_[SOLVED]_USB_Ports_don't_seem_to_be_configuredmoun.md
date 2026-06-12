---
title: "[SOLVED] USB Ports don't seem to be configured/mounted? bitpim"
date: 2007-07-09
forum: General Help
---

### Post by zabien1970 on 2007-07-09
I installed a program called bitpim that lets you acess a cellphone... when I run it I can't detect my phone,
It shows
=====Ports not available=====
USB Device - Vender Dell Computer Corp., Product Wireless 350 Bluetooth, (Interface #00)

This port is active but not available for use
Then there is some info about Property, Value, and Description which basically says my computer is using this device (Bluetooth) and the port is not available,

I have 4 USB plugs and none of them seem to recognise my phone plugged in, (I have the proper cable for my phone)

Reading through numerous forums it may be that the USB isn't mounted, no clue how to do this, but I could be wrong.

lsusb gives me this with the phone plugged in
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I'm using a Dell Inspiron 6000 and a LGVX8500 phone which is listed as supported by bitpim

I am a n00b so any help would be greatly appreciated, especially if its detailed

---

### Post by loserboy on 2007-07-09
the easiest way to test the ports would just be to hook a usb keyboard or mouse up to them and see what happens, that would narrow down.

---

### Post by zabien1970 on 2007-07-09
Unfortunately, I have nothing else, I'd hate to go buy something just to test a port

---

### Post by zabien1970 on 2007-07-09
Anybody, I've been workin' on this for a week, I'm a n00b and am totally lost here, I have figured out everything else but this!

---

### Post by loserboy on 2007-07-09
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth

is that the thing you are trying to get working? can it be moved to another port

---

### Post by zabien1970 on 2007-07-09
No, that's the only thing showing up, I plugged the phone through a USB cable into my laptop but I'm not getting anything.
 In the help section for bitpim it starts:
BitPim can access USB devices directly. This is done using libusb which accesses the usb filesystem. You need to ensure the filesystem (usbdevfs) is mounted, usually below /proc/bus/usb.

By default Linux configures USB devices so that they are owned by root. You should be running BitPim as yourself, not root. Most recent Linux distributions use hotplug, and these instructions show you how to configure it....
 
But I'm not sure how to do this, there are instructions but I don't know how to do things like edit scripts

---

### Post by loserboy on 2007-07-09
well according to [http://ubuntuforums.org/showthread.php?t=427464&highlight=Inspiron+6000](http://ubuntuforums.org/showthread.php?t=427464&highlight=Inspiron+6000)

the inspiron 6000 is supposed to work almost perfectly, and I've never seen anyone have a problem with the USB ports on one, so i think it's a different issue

---

### Post by zabien1970 on 2007-07-10
I don't think its an actual issue with the USB ports, the computer works beautifully, I am really impressed so far.
 I think it has to do with modifying something so the program/computer autodetects when the phone is plugged in.  There is instructions on the website about setting up USB in linux for this program but being new to the command line I need it broken down more, as in "add so and so to this and create that', I'm not sure how to do it or which directory I should be in.

---

### Post by loserboy on 2007-07-18
did you find an answer for this yet?

---

### Post by zabien1970 on 2007-07-27
Not yet, and to make matters worse I dropped my phone into a sewer at work, completely submerged for 2 min.! luckily I managed to take it apart and clean it with rubbing alcohol and after drying for two days it kinda works again but I would really like to get bitpim working so I can backup my info, I almost lost over 150 phone numbers.
  If you look at the linux instructions for bitpim there is a section for setting up USB, Unfortanately I'm just not familiar enough with the command line to figure it out, I'm sure it's something simple but I keep getting lost when the instructions say something like make sure you have 'this' in 'this file'.

---

### Post by zabien1970 on 2007-08-28
Finally had to get a new phone, got home, plugged it in, and it was detected right away, unfortunately verizon couldn't pull my phone list, apparently the plug in the phone was bad

---


---
title: "[SOLVED] bluetooth dongle with 7.10 in vmware"
date: 2008-01-02
forum: General Help
---

### Post by seesoe on 2008-01-02
hello all, I'm pretty much a high class noob (if such) when it comes to Linux, but recently for the past 3 days i learned a lot with Ubuntu.

i have got my computer to run GPSD with all LAMP programs and all that good stuff.
but the only thing i can't get to work is for my bluetooth dongle to be detected, so i can use that with my bluetooth GPS receiver for GPSD

now something that might be important (shouldn't though) that I'm running Ubuntu in vmware. how vmware works from what i understand should have anything to do with my problems.

the usb device is a generic one so i guess i need hci_usb.so for it

its not like this dongle can't be used with linux, because i have used it do try bluesnarfing in back|track with the same hci/bluez stuff, but i just can't get it to work with ubuntu

*btw i have all bluez tools install, install right im not sure if theres further configs to ubuntu need to be done.

---

### Post by scxtt on 2008-01-02
do you have a USB device added to the VM (and then enabled)?

---

### Post by seesoe on 2008-01-02
i plugged in a usb drive in the same port as where i had the bt dongle, and ubuntu saw that and opened up the flash drive automaticly.
 now when i do lsusb it shows

Bus 002 Device 002: ID 12f7:1a00  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

bus 2 device 2 is the usb drive
the other 2 should be the mouse and keyboard

i took the flash drive out and now

Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000

---

### Post by scxtt on 2008-01-02
i don't think the other 2 are "mouse and keyboard" - since the entries are **0000:0000** ... what does lsusb show when both the "usb drive" and the dongle are plugged in?

you generally have to explicitly enable the device in VMware ...

---

### Post by seesoe on 2008-01-02
OMG heaven!!!! lol. heres the setup.

dell with 2 usb in the front, and 4 usb in th back from a pci card

i had a extended usb cable with the bluetooth in going to one of the 4 ports from the pci card

then i had the usb mouse in the front, and usb webcam (forgot i had in)

ok so i took the webcam out and plugged the bluetooth in the front directly to the computer

and the flash drive in the extension cable in the back.

and i did lsusb to get

Bus 002 Device 003: ID 12f7:1a00  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 0e0f:0002  
Bus 001 Device 001: ID 0000:0000  

first on the list being the flash drive, second being the bluetooth other i donno for now but i know i see bluetooth and im good

im so exited now, i been working on this whole gpsd thing for a while now
thank you

TO ALL search the internet for a few days and forums like i did, try everything, even mess with the simple things like changing different ports!!! you never know what will work. if all fails post for help

---

### Post by John Stewart on 2008-03-21
I experinced problems with protection dongle in VMWare envronment. In the end I ordered [dongle emulator]("http://www.dongleservice.com") and use it without any problem. Not sure USB is really handled well enough in VMWare.

---


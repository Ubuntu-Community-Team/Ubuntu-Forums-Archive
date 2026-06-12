---
title: "SD Cards in Ubuntu"
date: 2007-01-03
forum: General Help
---

### Post by rioghal on 2007-01-03
I have several SD cards and when I put them into the card reader they get mounted automatically. The problem is one of them gets mounted to /media/MUSIC, another gets mounted to /media/BACKUPS, etc. I only have one card reader and would like to have all the SD cards mounted to /media/sda1 when I put them into the reader - regardless of which card I put in. What do I need to do to make that happen?

---

### Post by rioghal on 2007-01-05
*bump*

---

### Post by fragos on 2007-01-05
It would appear that something you installed in the past may have changed mounting rules.  The rules are contained in /etc/udev and /etc/udev/rules.d.  You will find that your card reader is actually a USB device.  One can't really gaurantee which of the rules files these rules may have been placed.  See if you can find any references to the unusual mount points you're seeing.  You might also look at the results of lsusb:

fragos@Geo:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:092e Logitech, Inc. 
Bus 004 Device 002: ID 04b4:120f Cypress Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:4d11 Hewlett-Packard 
Bus 001 Device 005: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 001 Device 001: ID 0000:0000 

The hex pairs identify vender:device and are used in some rules.  Sorry that I can only get you started.  I will see all posts you make to this thread and will attempt to answer specific questions for you.

---

### Post by macogw on 2007-01-05
The labels the individual SD cards have could be having an effect too.  There was a mention somewhere of how to change what the SD card is called.  Let me see if I can find it.

EDIT: This works on USB thumb drives, and maybe it'll work on your SD card too.

sudo apt-get install mtools
sudo mlabel /dev/sda1 new_label

change /dev/sda1 to wherever it's mounting at the time and give it a name.  Maybe it's seeing a name on the card which is making it think "oh, music, that goes THERE"

---

### Post by rioghal on 2007-01-06
> **macogw said:**
> The labels the individual SD cards have could be having an effect too.  There was a mention somewhere of how to change what the SD card is called.  Let me see if I can find it.

EDIT: This works on USB thumb drives, and maybe it'll work on your SD card too.

sudo apt-get install mtools
sudo mlabel /dev/sda1 new_label

change /dev/sda1 to wherever it's mounting at the time and give it a name.  Maybe it's seeing a name on the card which is making it think "oh, music, that goes THERE"
You know, I think you are correct. I use these SD cards in my Palm T|X and when the Palm formats the SD cards, it asks for a label. It seems that the Music card has the word "Music" for its label and Ubuntu mounts that card to /media/MUSIC. The same goes for the Backups card, it gets mounted to /media/BACKUPS. So, I am assuming that if I change all the labels to "sda1" then Ubuntu will mount them all to /media/sda1, is that a correct assumption?

I'll look at mlabel as well. Thanks for the info :)

---

### Post by rioghal on 2007-01-06
> **fragos said:**
> It would appear that something you installed in the past may have changed mounting rules.  The rules are contained in /etc/udev and /etc/udev/rules.d.  You will find that your card reader is actually a USB device.  One can't really gaurantee which of the rules files these rules may have been placed.  See if you can find any references to the unusual mount points you're seeing.  You might also look at the results of lsusb:

fragos@Geo:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:092e Logitech, Inc. 
Bus 004 Device 002: ID 04b4:120f Cypress Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:4d11 Hewlett-Packard 
Bus 001 Device 005: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 001 Device 001: ID 0000:0000 

The hex pairs identify vender:device and are used in some rules.  Sorry that I can only get you started.  I will see all posts you make to this thread and will attempt to answer specific questions for you.

the output of lsusb is:

[~ @ 07:05:28] lsusb
Bus 005 Device 002: ID 0781:b6b7 SanDisk Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I hope I didn't break something.

---

### Post by fragos on 2007-01-06
I looked into the label thing.  SDs will always be mounted as /media/{label} but there's nothing wrong with that because its a symbolic mount point linked to something like /dev/sda1 which refers to your physical card reader.  In your case the card reader manufacturer is SanDisk per the lsusb.  If your SD card had no label it would mount as /media/sda1.  If you click "Places" in the upper menu bar the drop down menu will offer to open your SD with Nautilus.  Assuming it was mounted as /media/MUSIC,  it will be called MUSIC and may even have an SD card for an icon.  Everything is working as it should.  You have no problem.

---

### Post by rioghal on 2007-01-06
> **fragos said:**
> I looked into the label thing.  SDs will always be mounted as /media/{label} but there's nothing wrong with that because its a symbolic mount point linked to something like /dev/sda1 which refers to your physical card reader.  In your case the card reader manufacturer is SanDisk per the lsusb.  If your SD card had no label it would mount as /media/sda1.  If you click "Places" in the upper menu bar the drop down menu will offer to open your SD with Nautilus.  Assuming it was mounted as /media/MUSIC,  it will be called MUSIC and may even have an SD card for an icon.  Everything is working as it should.  You have no problem.
Thank you for that information. I think I'll just keep the current setup and get used to the new mount points.

---


---
title: "USB drive issues"
date: 2008-04-30
forum: General Help
---

### Post by kgriff on 2008-04-30
I recently installed Hardy and, since then, have had issues with my USB HDD and flash drive.  I´ve seen posts with similar issues, though none seem to be having quite the same problems.  In any event, none of the suggestions in those posts have helped me.  If anyone has any ideas, I´d be grateful.

When I plug in a USB device, it appears to sometimes be recognized, and sometimes not.  If I reboot the machine with the drive connected, BIOS does recognize that it is there.
On the ocassions when it is recognized, it is sometimes automounted, and sometimes not.  When it is recognized, and not automounted, I cannot mount it manually.

So far, I have only had it recognized once, not automount, and fail to manually mount.  Perhaps unfortunately, on that ocassion, I tried to manually mount it in gnome, rather than in terminal, so I don´t know what errors I would have seen in terminal.

One additional bit of data:  I also have an external 4 port USB hub with an HP printer connected.  This is one of the HP printers with all of the built in media readers.  The system recognized both of these devices every time, though I haven´t tried to use the printer yet.

I just tried plugging the flash drive into the external hub, and even though the system sees the HP printer, it does not see the flash drive.  It does not even power up the flash drive.

New error:  I switched users with the USB HDD connected.  As soon as I could see the desktop on the second user, there was an error message, ¨failed to initialize HAL!¨

---

### Post by kgriff on 2008-04-30
Update:
I tried this same HDD and flash drive on another computer also running Hardy.  Both worked perfectly.  Is there a way to check and see what isn´t working correctly with the USB on the improperly functioning machine?

---

### Post by Bloch on 2008-05-01
Here's a general solution that works with mounting issues. Unfortunately it's command-line, and I do wish the automount worked in a more consistent way.

Plug in your memory device. If it doesn't automount then:

1. Open a terminal. Enter
```
sudo fdisk -l
```
(you will need to type you password)

2. You will see a list of the "disks" and their partitions and their location 
e.g. /dev/sda1    /dev/sdb1  /dev/sdc2 etc

Find the device you plugged in - if it is a memory stick the "System" might be labelled as  W95 FAT32. Or you can judge it by the size of the memory. The device will have a number: /dev/sdb1 /dev/sdb2 etc, not simply /dev/sdb

2. Mount it using the 'pmount' command. Here is an example where /dev/sdc2 was my memory stick 
> pmount /dev/sdc2 any_name_you_like

You need to have pmount installed. Install it using synaptic, or your favourite method.
pmount will mount this at the location
/media/any_name_you_like

So you go to that directory and open it. Or click "Computer" on the nautilus window.

Alternatively you can use the "mount" command, but with pmount you don't have to create the mount directory in advance. pmount will create the directory /media/any_name_you_want

---

### Post by kgriff on 2008-05-03
If the device is recognized when it is plugged in, it appears to always automatically mount.  The issue is that Ubuntu does not even recognize that a USB device has been plugged in.  In this case, I cannot see it using fdisk.  I can't even see it using ls usb.  It is simply ignored when plugged in.  The device is powered on by the usb port, but the system does not recognize that anything has been plugged in.

This would not be a big deal if it was my computer, because I rarely use external devices like this.  However, this is my wife's machine and she uses an external HDD as well as an IPod.

Anybody have any other suggestions?

---

### Post by argosreality on 2008-05-03
When you plug in your drive and its not recognized can you check the contents of your /var/log/dmesg and syslog files? If you're seeing a ton of reset lines in there then you're not alone. 

No idea of a fix at the moment though

---


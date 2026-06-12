---
title: "Problem accessing external USB hard-drive (Maxtor)"
date: 2006-07-28
forum: General Help
---

### Post by espenbe on 2006-07-28
I just bought an external USB hard-drive (Maxtor personal storage 3200), but I can't get it to work with my Kubuntu 6.06.  I don't know what is wrong.  Here is some output:

```
espenbe@ball-9164:~$ dmesg|tail
[17180870.644000] usb 4-2: new full speed USB device using uhci_hcd and address 4
[17180870.764000] usb 4-2: device descriptor read/64, error -71
[17180870.988000] usb 4-2: device descriptor read/64, error -71
[17180871.204000] usb 4-2: new full speed USB device using uhci_hcd and address 5
[17180871.324000] usb 4-2: device descriptor read/64, error -71
[17180871.548000] usb 4-2: device descriptor read/64, error -71
[17180871.764000] usb 4-2: new full speed USB device using uhci_hcd and address 6
[17180872.172000] usb 4-2: device not accepting address 6, error -71
[17180872.284000] usb 4-2: new full speed USB device using uhci_hcd and address 7
[17180872.692000] usb 4-2: device not accepting address 7, error -71

```


```
espenbe@ball-9164:~$ tail /var/log/messages
Jul 28 16:36:25 ball-9164 kernel: [17180739.880000] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jul 28 16:36:25 ball-9164 kernel: [17180740.020000] hub 4-1:1.0: USB hub found
Jul 28 16:36:25 ball-9164 kernel: [17180740.024000] hub 4-1:1.0: 4 ports detected
Jul 28 16:36:26 ball-9164 kernel: [17180740.352000] usb 4-1.2: new low speed USB device using uhci_hcd and address 3
Jul 28 16:36:26 ball-9164 kernel: [17180740.520000] input: Logitech Optical USB Mouse as /class/input/input4
Jul 28 16:36:26 ball-9164 kernel: [17180740.520000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-1.2
Jul 28 16:38:36 ball-9164 kernel: [17180870.644000] usb 4-2: new full speed USB device using uhci_hcd and address 4
Jul 28 16:38:37 ball-9164 kernel: [17180871.204000] usb 4-2: new full speed USB device using uhci_hcd and address 5
Jul 28 16:38:37 ball-9164 kernel: [17180871.764000] usb 4-2: new full speed USB device using uhci_hcd and address 6
Jul 28 16:38:38 ball-9164 kernel: [17180872.284000] usb 4-2: new full speed USB device using uhci_hcd and address 7

```

```
espenbe@ball-9164:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 004 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

Because of this, I don't know how to access it to format it or mount it.  Any wizards who can give me any clues?

Espen

---

### Post by s_h_a_d_o_w_s on 2006-07-28
You want to format it? Do you want to install kubuntu on it? then go into BIOS and choose "USB" as primary boot device, instead of your hard drive. Im not sure if that is what you mean.

---

### Post by uberground on 2007-05-31
I just bought one myself. Headed over to [http://njoubert.blogspot.com/2006/11/woops-slip-bonk.html](http://njoubert.blogspot.com/2006/11/woops-slip-bonk.html) and found out it was formatted to NTFS, so a friend connected it up to a Mac and erased the partition and put on FAT32 (easier than messing with gparted).  Automatically mounts now, sweet.  Could it be the messages you're receiving are a red herring? Check it out on a windows box, ran fine for me without additional drivers on XP & Vista (still runs fine after having FAT32, but early days yet)

---

### Post by Caydel on 2007-09-15
I am having similar issues while trying to access an external disk  on my system. The relevant dmesg lines are:

```
[ 6028.840000] usb 3-2: new full speed USB device using ohci_hcd and address 7
[ 6032.028000] usb 3-2: device descriptor read/64, error -110
[ 6047.320000] usb 3-2: device descriptor read/64, error -110
[ 6047.612000] usb 3-2: new full speed USB device using ohci_hcd and address 8
[ 6050.800000] usb 3-2: device descriptor read/64, error -110
[ 6066.092000] usb 3-2: device descriptor read/64, error -110
[ 6066.384000] usb 3-2: new full speed USB device using ohci_hcd and address 9
[ 6076.792000] usb 3-2: device not accepting address 9, error -110
[ 6076.980000] usb 3-2: new full speed USB device using ohci_hcd and address 10
[ 6087.388000] usb 3-2: device not accepting address 10, error -110
```

and from lsusb:

```

Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c03d Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

What could be causing these errors? This drive worked fine on a fresh install not so long ago. However, it seems to start erroring out once I update the system's packages.

Any thoughts?

---

### Post by Eskokk on 2007-09-23
I had just similar error messages when plugging in my usb Samsung drive. Turned out to be wrong hard drive jumper settings on my case. I changed them to "cable select" and after this it works ok.

---

### Post by jimi.vicious on 2007-10-01
> **espenbe said:**
> I just bought an external USB hard-drive (Maxtor personal storage 3200), but I can't get it to work with my Kubuntu 6.06.  I don't know what is wrong.  Here is some output:

Because of this, I don't know how to access it to format it or mount it.  Any wizards who can give me any clues?

I recently purchased this exact same drive (formatted with NTFS - yuck!), and got exactly the same errors as yourself. Ubuntu refused to have anything to do with it. Even gPartEd wouldn't pick it up. It worked fine in Knoppix though, which I used to format it as Fat32.

Then, completely by chance I unplugged my 4-port hub from a neighbouring port and the Maxtor sprang into life. Ubuntu now sees the drive, and automounts perfectly. Strange but true.

My advice is to unplug your USB devices one by one to see if something is conflicting.

Good luck! :D

---

### Post by digitalramble on 2007-10-01
I'm suddenly getting this as well, with an external drive that worked fine up until a few weeks ago.  dmesg shows that same error -71 as in the initial message.    Thoughts?

---

### Post by styelz on 2008-06-25
I had similar problems with my extranal USB drive except with the following error.

"device not accepting address 6, error -32"

I found that the USB devices had been disabled by the motherboards "curciuit protection". I was able to reset this by unpluging the Power Supply Unit from the motherboard. All USB's came back to life after this.

I am going to try a more powerfull PSU and see if it solves the problem as the USB's seem to fail when both my PCI DVB capture cards are running.

Good Luck!

---


---
title: "Troubles with mp4/mp3 player."
date: 2007-04-22
forum: General Help
---

### Post by The Creator on 2007-04-22
Hello, 

I just bought an mp4 player from ebay (a nock off ipod) and it ran perfectly under windows, detected and everything without any additional drivers and same for os x. I just installed ubuntu to find that it wasnt working anymore. You put files on it just like any other mp3 player on to the fat32  usb drive that it shows up as. I am running ubuntu 7 and i tried installing that microsoft protocol thing that is supposed to fix this but it didnt help. Any help would be greatly appreciated and thanks in advance :)

The Creator

---

### Post by heimo on 2007-04-22
You should at least add make and model of the device and perhaps output of "lsusb" when the device is connected. I don't have good experiences with non-standard music players.

---

### Post by The Creator on 2007-04-22
john@john-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

there you go, the mp3 player sais it is connected and it works under hackint0sh too. I tried plugging in a usb flash drive just to make sure my usb works and it does.

edit: i used to have a creative zen nano and it connects exactly the same way under other os's. And the format for the player is fat32.

---

### Post by heimo on 2007-04-22
That doesn't show any devices. See my example below (four USB devices connected).
```

Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 058f:9380 Alcor Micro Corp. Flash drive
Bus 003 Device 003: ID 0ccd:0028 TerraTec Electronic GmbH 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0ace:1201 ZyDAS 802.11b WiFi
Bus 005 Device 003: ID 056a:0015 Wacom Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

Try running "tail -f /var/log/messages" in a terminal while plugging in your device and show us all the output (and go Google with those device IDs if anyone had any solutions for your device). It may not be driver related. What's the model of your device?

---

### Post by The Creator on 2007-04-22
the output is:

```

Apr 22 00:02:36 john-laptop kernel: [ 2389.188000] usb 3-4: new high speed USB device using ehci_hcd and address 65
Apr 22 00:02:36 john-laptop kernel: [ 2390.448000] usb 3-4: new high speed USB device using ehci_hcd and address 69
Apr 22 00:02:37 john-laptop kernel: [ 2391.960000] usb 3-4: new high speed USB device using ehci_hcd and address 74
Apr 22 00:02:39 john-laptop kernel: [ 2393.472000] usb 3-4: new high speed USB device using ehci_hcd and address 79
Apr 22 00:02:43 john-laptop kernel: [ 2397.000000] usb 3-4: new high speed USB device using ehci_hcd and address 92
Apr 22 00:02:46 john-laptop kernel: [ 2401.032000] usb 3-4: new high speed USB device using ehci_hcd and address 107
Apr 22 00:02:48 john-laptop kernel: [ 2402.292000] usb 3-4: new high speed USB device using ehci_hcd and address 111
Apr 22 00:02:48 john-laptop kernel: [ 2402.796000] usb 3-4: new high speed USB device using ehci_hcd and address 112
Apr 22 00:02:50 john-laptop kernel: [ 2404.812000] usb 3-4: new high speed USB device using ehci_hcd and address 119
Apr 22 00:02:53 john-laptop kernel: [ 2407.584000] usb 3-4: new high speed USB device using ehci_hcd and address 3
Apr 22 00:02:55 john-laptop kernel: [ 2409.852000] usb 3-4: new high speed USB device using ehci_hcd and address 11
Apr 22 00:02:57 john-laptop kernel: [ 2411.616000] usb 3-4: new high speed USB device using ehci_hcd and address 17
Apr 22 00:03:02 john-laptop kernel: [ 2416.152000] usb 3-4: new high speed USB device using ehci_hcd and address 34
Apr 22 00:03:07 john-laptop kernel: [ 2421.444000] usb 3-4: new high speed USB device using ehci_hcd and address 54
Apr 22 00:03:09 john-laptop kernel: [ 2422.956000] usb 3-4: new high speed USB device using ehci_hcd and address 59
Apr 22 00:03:10 john-laptop kernel: [ 2424.216000] usb 3-4: new high speed USB device using ehci_hcd and address 63
Apr 22 00:03:12 john-laptop kernel: [ 2426.988000] usb 3-4: new high speed USB device using ehci_hcd and address 73
Apr 22 00:03:17 john-laptop kernel: [ 2431.776000] usb 3-4: new high speed USB device using ehci_hcd and address 91
Apr 22 00:03:19 john-laptop kernel: [ 2433.036000] usb 3-4: new high speed USB device using ehci_hcd and address 95
Apr 22 00:03:20 john-laptop kernel: [ 2434.296000] usb 3-4: new high speed USB device using ehci_hcd and address 99
Apr 22 00:03:23 john-laptop kernel: [ 2437.068000] usb 3-4: new high speed USB device using ehci_hcd and address 109
Apr 22 00:03:25 john-laptop kernel: [ 2439.588000] usb 3-4: new high speed USB device using ehci_hcd and address 118
Apr 22 00:03:26 john-laptop kernel: [ 2440.092000] usb 3-4: new high speed USB device using ehci_hcd and address 119
Apr 22 00:03:29 john-laptop kernel: [ 2443.872000] usb 3-4: new high speed USB device using ehci_hcd and address 7
Apr 22 00:03:30 john-laptop kernel: [ 2444.880000] usb 3-4: new high speed USB device using ehci_hcd and address 10


```

It doesn't seem to have a model number that i can see. Thanks for the help so far :)

---

### Post by heimo on 2007-04-22
Let's try another approach. You say:

> **The Creator said:**
> and i tried installing that microsoft protocol thing that is supposed to fix this but it didnt help.

What do you mean? Do you have links to this?

---

### Post by The Creator on 2007-04-22
[http://libmtp.sourceforge.net/]("http://libmtp.sourceforge.net/")

---

### Post by heimo on 2007-04-22
Well. Without model of the device, I'm lost. Personally, at this point, I'd return the device and get something that's supported without proprietary drivers or programs, out of the box (by transferring files to to device as if it was a USB memory stick).

---

### Post by The Creator on 2007-04-22
it doesnt require drivers that are proprietary. It works just like a usb memory stick. It has samsung membory in it and plugs in just like any other mp3 player. This is the same as a usb drive not being recognised.

---

### Post by 3rdalbum on 2007-04-22
You don't need libmtp.

I've had this exact problem with a hard disk MP3 player on Puppy Linux - same list of "device detected" messages and everything. There doesn't seem to be any way of fixing it; really, just try a different distribution.

---

### Post by heimo on 2007-04-22
> **The Creator said:**
> it doesnt require drivers that are proprietary. It works just like a usb memory stick. It has samsung membory in it and plugs in just like any other mp3 player. This is the same as a usb drive not being recognised.
Oh! :) On the device, find settings. Find transfer mode (or what ever it's named), change it to the other setting. Retry. (with this I'm referring to a setting where one option is to use MTP - use the other)

---

### Post by The Creator on 2007-04-22
but, but but.... ubuntu is so perfect! please dont make me go back to windows!

---

### Post by heimo on 2007-04-22
> **The Creator said:**
> but, but but.... ubuntu is so perfect! please dont make me go back to windows!

I don't know if you're serious or not. For me, not being able to use one device, wouldn't be a reason to change my operating system.

---

### Post by The Creator on 2007-04-22
ok, i just plugged it in under mac os. 

USB 2.0(HS) Flash Disk:

  Version:	1.00
  Bus Power (mA):	500
  Speed:	Up to 480 Mb/sec
  Product ID:	0x1101
  Serial Number:	A00000600001
  Vendor ID:	0x10d6

---

### Post by kvonb on 2007-04-22
I read a bug post which might coincide with your problem.

The USB device is not being recognised by Feisty, you could try booting a copy of Ubuntu 6.06 or even 6.10 to see if it works under those versions.

If my theory is correct, it is something to do with the devs disabling a certain part of the USB library in order to get suspend working properly with laptops for the Feisty release date.

They had no choice apparently, as most laptop users would have been left out.

My Canon 1240 scanner did the same thing, it didn't even show up in the USB list, the problem is that I then assumed that the scanner was broken and promptly threw it in the bin!!!!

I was not amused I can tell you!

But they are working on fixing it, and it will come as an update once it's fixed.

Regards, Kev :)

---

### Post by The Creator on 2007-04-22
i dont really need suspend on my laptop, is there a way i can reverse their change?

---

### Post by heimo on 2007-04-22
Just for reference, is this the device?
[http://www.mympxplayer.org/pafiledb/images/screenshots/27732481fullnb8.jpg](http://www.mympxplayer.org/pafiledb/images/screenshots/27732481fullnb8.jpg)
[http://www.mympxplayer.org/image-df414.html](http://www.mympxplayer.org/image-df414.html)

---

### Post by The Creator on 2007-04-22
no, it isnt. It is a nockoff from honkong. It may have the same components in it though.

---

### Post by The Creator on 2007-04-22
I think that ill just dual boot with windows and that way i can access it from my laptop. Then when the update comes out ill delete the windows partition. How does that sound?

---

### Post by heimo on 2007-04-22
Try finding a setting in your device which says "MTP" and change it to "MSC" if it's available.

---

### Post by The Creator on 2007-04-22
it isnt there :(

---

### Post by The Creator on 2007-04-22
I am sorry but this is the point where i decide to give up. Ill just install windows on my laptop and keep ubuntu on my other computers. Thanks all for your help. Best of wishes. :)

---


---
title: "MP3 Player mounting woes"
date: 2008-01-12
forum: General Help
---

### Post by Nexusx6 on 2008-01-12
Hey all, I'm at wits end and really needing help :frown:

I have a Samsung YP-T9J that I've tried to mount for over an hour now with not even a glimer of getting any closer. Googled the problem 6 ways to sunday and haven't found an answer. When I plug the MP3 player in, Rythem Box opens, but shows no media at all, and its not being mounted automatically anywhere. Furthermore, dmesg sheds no light on where the thing is in the system /sigh. Any and all help is appreciated.

```
fox@aurora-project:~$ dmesg | tail
[   46.461085] /dev/vmnet: port on hub 8 successfully opened
[   49.833284] NET: Registered protocol family 10
[   49.833342] lo: Disabled Privacy Extensions
[   49.833742] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   59.833094] vmnet1: no IPv6 routers present
[   59.845056] vmnet8: no IPv6 routers present
[   60.128255] eth0: no IPv6 routers present
[  620.956472] usb 2-7: USB disconnect, address 5
[  633.592028] usb 2-7: new high speed USB device using ehci_hcd and address 6
[  633.727596] usb 2-7: configuration #1 chosen from 1 choice

fox@aurora-project:~$ lsusb 
Bus 002 Device 006: ID 04e8:507f Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c221 Logitech, Inc. 
Bus 001 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c222 Logitech, Inc. 
Bus 001 Device 002: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```


**______SOLUTION:______**
I'm posting this in the event that someone else might find this useful. I found the solution to my problem, though it took way.. **way** longer than it should have to find, and more aspirin too.

The whole big ugly problem wasn't the filesystem on the MP3 player, but in fact MTP. Media Transfer Protocol is an ugly mess of M$ junk that makes life hell for both Linux users and in fact Windows as well and is part of M$ DRM loaded "plays for sure" garbage. That said, the solution is to get ride of that trash, and load your MP3 player with (dun da da daa) open source protocols! Specifically -- UMS. 

If your MP3 player doesn't support UMS off the shelf (like T9 Samsungs) you can usually fix that with a  hacked/crack firmware update. Best place to look for this is in the [www.anythingbutipod.com](www.anythingbutipod.com) forums. Unfortunately, because your MP3 player is un-mountable as is, you'll have to do this firmware update from a Windows machine. Hope this help someone ^^ If you're having trouble figuring this out, feel free to PM me.

---

### Post by dcstar on 2008-01-12
> **Nexusx6 said:**
> Hey all, I'm at wits end and really needing help :frown:

I have a Samsung YP-T9J that I've tried to mount for over an hour now with not even a glimer of getting any closer. Googled the problem 6 ways to sunday and haven't found an answer. When I plug the MP3 player in, Rythem Box opens, but shows no media at all, and its not being mounted automatically anywhere. Furthermore, dmesg sheds no light on where the thing is in the system /sigh. Any and all help is appreciated.
.........

If the device is formatted in a filesystem that Ubuntu cannot support, then it cannot be mounted.

Do you know what it is formatted in?

---

### Post by Nexusx6 on 2008-01-12
> **dcstar said:**
> If the device is formatted in a filesystem that Ubuntu cannot support, then it cannot be mounted.

Do you know what it is formatted in?

I was starting to suspect this might be an issue. I don't know what the file format is, nor how to check it.

---

### Post by Nexusx6 on 2008-01-13
Is there a way I can view and/or format my MP3 Player's file system? I've tried gParted and QTparted but neither of them see my player :( Any tips?

---

### Post by Nexusx6 on 2008-01-14
Found a solution to my problem! I edited Original Post with the fix

---

### Post by Sonja on 2008-01-16
Is there a hacked/crack firmware update for Samsung YP-U2JB/XAC that will work in Ubuntu? Thanks for the help. I'm an Ubuntu n00b and don't know where to look it up.

---

### Post by Nexusx6 on 2008-01-16
I was trying to help you, but the "YP-U2JB/XAC" doesn't seem to exist anywhere :confused:
Are you sure you typed in your model number correctly? A search for the "YP-U2JB/XAC" on Google and Samsung returns nothing but "Cannot Be Found" errors. Have a look again if you will please, and make sure that model number is correct :) If you can't find it anywhere, try linking me to your player on the net.

---


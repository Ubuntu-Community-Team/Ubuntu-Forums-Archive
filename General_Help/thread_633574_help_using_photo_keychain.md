---
title: "help using photo keychain"
date: 2007-12-06
forum: General Help
---

### Post by gspat on 2007-12-06
I bought a couple innovage photo keychains to give as gifts this christmas, but can't get them working...

ok, it DOES say for use with PC and MAC only, but it should still work as a USB drive to load pictures to it.

I tried using wine to install the program, but it does not recognise the darn thing...

lsusb shows it is there!

```
gspat@Home:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1403:0001  <-- this is it...
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04b3:300a IBM Corp. 
Bus 001 Device 001: ID 0000:0000  
gspat@Home:~$ 

```

I also tried various other programs, thinking it might respond as a camera using PTP (I think that was the name of the transfer method) but that did not work either, so gphoto2 didn't help me...

anyone have any ideas as to to try next? 

All I wanna do is load so pics of the kids on it for the inlaws!

using ubuntu 7.10

---

### Post by jbaas on 2007-12-10
I just bought one too, haven't had any luck on ubuntu either, did find this page: [http://gkall.hobby.nl/dpf018.html](http://gkall.hobby.nl/dpf018.html) so there is at least someone working on it...

Can't even get it to work on OSX, so pretty much useless to me.

---

### Post by tragicglee on 2007-12-10
> **gspat said:**
> but it should still work as a USB drive to load pictures to it.

Not owning one myself, I'm clueless... but have you tried mounting it and copying the images manually? If you have a Windows CD laying around, install virtualbox, create a VM and load it up through that (semiridiculous for sure, but desperate times call for desperate measures, and the keychain may depend on the software to either format the pictures properly, or convert them to a silly proprietary format of some sort). 

I tend to avoid picking up things like this prior to researching because it often results in more frustration than it's worth. I do have access to Windows, but hate being forced to use it - in my world, hardware works for me, I don't work for it. Oh  look, I'm ranting. *shuts up* :(

Good luck!

---

### Post by wirah on 2007-12-10
Hehe - Just bought five of these myself from ebay and yep,

1403:0001 is the USB Bus ID.

I quite fancy writing a driver for this myself, but I can't be bothered to install windows to figure out how the supplied driver works!

Might try looking up some old pendrive instructions and see if those work.

How do I submit an entry for this BusID. I'm ready to take it apart and figure out the manufacturer - says it's RoHS compliant.

Loving the device though, who knew you'd be able to carry round a 1.5" LCD screen in your pocket!

---

### Post by jbaas on 2007-12-13
I installed windows in a virtual machine to put pictures on there, bit of a hassle, but the only way I guess.

Yesterday an Apple version of the software popped up: [http://www.dpf001.nl/DPF_001_files/Setup%20for%20Apple%20OSX.dmg](http://www.dpf001.nl/DPF_001_files/Setup%20for%20Apple%20OSX.dmg) but it crashes on my macbook right after showing the window.

The device does offer usb-storage access, but with a bogus partition table, and I couldn't make any sense of the filesystem as well. Also the advertised disk is only 2MB, this should be 8MB right?

---

### Post by wirah on 2007-12-17
I dropped them a quick email and offered to write a driver if they could provide the source code. However, they were not willing to provide source code which makes it very difficult :(

Their email is below

----

Dear mr. Jones,

Thank you for the interest in our product.
While we value your offer, we are not able to provide the source code of our programs. At some point in time we might, however, make a Linux version available. At the moment, there are no definite plans, though.

In the mean time, I would suggest using a Windows emulator to achieve the same result.


Kind regards,

Allart van Holten

KMB Europe BV
[email]info@kmb-europe.nl[/email]
Tel. +31 (0)20 647 9760
Mob. +31 (0)6 52455 000

---


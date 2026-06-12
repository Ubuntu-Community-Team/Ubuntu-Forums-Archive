---
title: "[SOLVED] Last call on USB error -110"
date: 2008-02-15
forum: General Help
---

### Post by Phosphoric on 2008-02-15
Somebody must have an answer to what this error means when booting up Feisty or Gutsy:

device descriptor read/64, error -110

It repeats for several lines with  a different ID number at the front each time.

The upshot of this error is that I have extreme difficulty connecting to my printer and very slow recognition of a camera when plugged in.

Typing "lsusb" in the terminal eventually spots all of my attached USB devices correctly, but takes ages to do it.

I have raised and contributed to 3 other threads on this subject and there have been no solutions forthcoming.

My hardware works fine under Windows XP, instant and correct recognition.

The problem occurs under live CD of Gutsy and Feisty and I also tried Linux Mint, all the same problem.  

This started happening just a few weeks ago after I was fiddling around with a USB stick and had a problem ejecting it.


This is so strange, the fact that the problem is repeated under 3 diefferent live CDs  indicates a hardware problem to me, but a dreaded dual boot back in to Windows gives me perfect USB functionality so it can't be hardware.  :confused::confused::confused:

---

### Post by jeffus_il on 2008-02-15
Do you remember the changes you made when "fiddling around with a USB stick" ?

---

### Post by Phosphoric on 2008-02-15
As I, when I unplugged the pen drive, I got a message saying that I could lose data if I didn't eject the drive properly.  I couldn't find the option to eject but did come across an unmount command which I clicked on.

Thing is,  whatever I might have done wrong, surely shouldn't affect a live CD installation?

---

### Post by TxsFireman on 2008-02-15
I think I am having the same problem.  I just installed ubuntu 7.10 as a dual boot with windows xp on my Toshiba laptop.  My usb's have not worked since installation on ubuntu, but work fine in xp.  If I have my mouse plugged in during startup it works but it is choppy, very slow and "skips" across the screen.  If I unplug and plug back in or just plug in after startup it does not work at all.

---

### Post by Phosphoric on 2008-02-15
Update on camera recognition:

When I plug my camera in it is immediately recognised that "a camera" has been plugged in but then says "no camera detected"  However, I have now spotted that in another box is a message:"  Loading camera driver from /usr/lib/libgphoto2/2.3.0'...."

This is what is taking ages.  Eventually the driver is found and I can carry on as usual. 

If I unplug the camera and plug it back in again, the driver appears to have been lost and it takes ages to find it again.

Does that pose any further clues?

---

### Post by Phosphoric on 2008-02-21
Well   sort of solved.

After much frustration and dabbling back on the dark side, I decided to apply some rigorous logic.

Bought a powered USB hub....waste of money:(

Plugged in every single device in every combination and I think..... the problem is down to a faulty external hard drive.  This is a Western Digital drive that can be connected by firewire or USB.  It always used to work OK but now for some reason or other the USB connection seems to be giving me these problems in Ubuntu only.  I reiterate that Windows XP has no problem hence my only half a mark for being solved.

 Disconnected the USB cable from the external drive and everything else works as it should.  Luckily the external drive works fine on firewire (unlike my DV video capture from my camcorder)

So I'm back up and running with Ubuntu but still feeling a little like a poor relation in that my hard drive works perfectly in Windows but not Ubuntu.

Hope this helps all the other people with this error who have had no useful replies.

---

### Post by fjgaude on 2008-02-21
I had a USB flash card reader that stopped by machine from booting with tha t -110 error. I upplugged the reader and it booted. I went and bought an identical one and all has been fine.

Go figure...

---


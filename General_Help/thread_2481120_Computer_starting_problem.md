---
title: "Computer starting problem"
date: 2022-11-19
forum: General Help
---

### Post by jgw on 2022-11-19
I have a computer that doesn't want to boot.  What happens is that it tells me to connect to the boot disk and then press a key.  What happens is that every time the computer is shut down for an hour or more and then I try and start it I get the same thing.  My solution is to remove the power supply to ssd that holds the boot stuff, and then plug it back in.  II have found how to restart the machine.  I have to disconnect the ssd and then connect it again.  As far as I can tell it doesn't matter which I disconnect and connect - power or data, both work.  This makes absolutely no sense to me.  I have tested the power side to see if its alive before plugging it back in and its always powered up.  

I have no idea how to fix this.  My current method is to have the computer case open so I can remove and replace any single plug plug of the two plugged into the ssd. I have also taken out the ssd and tested it as an external ssd and everything seems to be fine.  

Thank you.............

---

### Post by aljames2 on 2022-11-19
It may help if you share what OS(s) is/are installed on the SSD (if any).  What are your boot intentions.  Are you trying to do a new installation?  Are there any other storage devices connected, if so you could try disconnecting those leaving only your subject SSD connected.  The Bios can sometime prioritize storage devices different than you expect.

---

### Post by ne29914 on 2022-11-19
Sounds like you have a dead CMOS battery. Easily fixed.

---

### Post by jgw on 2022-11-19
Thank you for the replies!

I assume that CMOS battery refers to the battery on the motherboard.  The battery was fine but, just to make sure, I put in a new one.  Nothing changed.

I also tried removing and replaced the data connection on the ssd and nothing changed.

so, I removed the power, while running, from the ssd and put it back in and re-booted and it booted just fine. 

I also unconnected my other drive to see if that made any difference - nothing changed
I also set my other drive to not boot on start - nothing changed
I then turned off the machine and THEN pulled the power off, and then on the ssd - then I restarted and, it booted!

So it booted when the power was unplugged and plugged wheither the machine was running or not!
The booting was slightly different - it gave my an authorization request before it finished - none of this makes any sense to me!

Just to make sure I just turn it off and turned it back on - It didn't boot and told me that needed to connect a proper boot drive and then press a key.
When the key is pressed nothing happens.  I had to connect and dis-connect the power from the ssd and then press the ^c/alt/del and then it booted right up.
It continues to make no sense.

Processor	        AMD A8 PRO-7600B R7, 10 Compute Cores 4C+6G
Memory	                15297MB (2805MB used)
Machine Type	        Desktop
Operating System	Ubuntu 22.04.1 LTS
Total Memory	        15297588 KiB
Boot Drive:              ATA SSD 1TB

---

### Post by jgw on 2022-11-20
I may have found the problem  I swapped out my power supply and now it seems to be booting without a problem!  I should have done that before I started this but I didn't and I apologize as, on reflection, that's probably the first thing I should have done!

Anyway, thank you for the thoughts and I will mark this one solved............

---


---
title: "Computer freezes and doesn't boot consistently."
date: 2013-07-15
forum: General Help
---

### Post by cwblanch on 2013-07-15
Hi,[INDENT=2]Sorry for the long post, but I don't know how to explain it more simply or what information to include.
[/INDENT]

[INDENT]I'm guessing this is a hardware issue, but I simply don't have enough hardware knowledge to know what it is specifically.
I got a computer from a friend, an old junker of his, and at first everything seemed fine. I installed Ubuntu and Windows and everything was fine until it would just stop working for no reason that I could find. I did another new installation of both OSes and the problem is persisting. It will even freeze in the BIOS!!
All I can do is guess at what the problem could be, and have no idea how to test them.
A few internet searches say RAM or motherboard issue, but I'm getting errors on start up about hd:0 or unable to find filesystem. It's difficult to get a consistent error because it either doesn't boot at all and I have to try again or the error changes OR it might actually start up for a few minutes.
My only other guesses are the power, battery or hard drive.

Any help is very appreciated as I have no idea what's going on or how to fix it.

Thanks!
[/INDENT]

---

### Post by bcschmerker on 2013-07-16
The first problem to rule out is the power supply, as it will most definitely affect the system at power-on self-test and defeat attempts at core hardware settings.  I recently replaced a decade-plus-old Athena® P4ATX50FE (500W total load, predates 80 Plus standard) on my custom LinUX box in a modified Everex® TC2502 case (I call it the "Hot Rod gPC®" - Gigabyte® GA-MA78GM-S2HP, Advanced Micro Devices® Athon 64® X2 5600+), with an Antec® TruePower® 750 Blue to head off similar problems to yours - the P4ATX50FE's +3.3V bus was down to 2.965 VDC when last run, versus the TP-750's 3.341 VDC (as of this Post).

The next possible causes are inter-related.  The CPU and chipset have to work as a team, and a CPU that post-dates support from the BIOS on the motherboard will probably have erratic performance no matter what OS is on the hard drive.  If the CPU checks out with the BIOS, does your system have an 8&#8486; speaker on the Front Panel harness?  It may be needed for the pseudo-Morse codes for hardware problems detected early in the power-on self-test.

---

### Post by cwblanch on 2013-07-16
I'm sorry. I forgot to say that this is a laptop. 
I just tried switching out hard drives, and it still froze up...so I guess that's not it?
Thank you for your help though

---

### Post by cwblanch on 2013-07-17
Yesterday I also downloaded and used Memtest86 for about 6 hours and no errors came up. 
Does that mean that it is not the RAM at all? Or is there some other test I haven't found?

---


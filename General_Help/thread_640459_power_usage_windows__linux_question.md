---
title: "power usage windows / linux question"
date: 2007-12-14
forum: General Help
---

### Post by dronepower on 2007-12-14
Something is puzzling me.

I have a system having a A64 3000+ venice processor, 1GB RAM, Asus AV8 board, a Nvidia 6800LE and a 500GB seagate drive.

Under windows XP idling it uses 78Watt, but with a Ubuntu Live CD is uses 9 Watt less ; 69Watt idling.

Then I found this review saying Ubuntu uses more than windows xp :confused:

[http://www.phoronix.com/scan.php?page=article&item=880&num=2](http://www.phoronix.com/scan.php?page=article&item=880&num=2)

What are your experiences?

---

### Post by njparton on 2007-12-14
Did you have to buy something to check your power consumption or use a piece of software?

---

### Post by dronepower on 2007-12-14
I'm using a watt meter connected on the socket where the pwoe supply has been plugged in.

---

### Post by tgalati4 on 2007-12-14
It's quite possible.  Throttling and frequency control daemons are installed but I don't think they are activated by default.  You will have to do some searching in the forums for your specific processor.

Also, power settings in the BIOS can interact with Linux in different ways.  For older processors (such as Pentium D) using the "Auto" power settings in the BIOS will save ~10 watts over the "Normal" setting in Linux.  I can only guess that Linux recognizes the BIOS savings mode and the BIOS performs some sort of frequency/voltage control at the hardware level.  Seems to work.

---


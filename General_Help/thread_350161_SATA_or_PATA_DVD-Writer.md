---
title: "SATA or PATA DVD-Writer?"
date: 2007-01-31
forum: General Help
---

### Post by johann_p on 2007-01-31
I am trying to get Ubuntu 6.10 running on my new computer, which has a DG965WH mainboard with a Core2 Duo processor. 
This computer has an IDE DVD writer attached to the PATA  port on the mainboard and I have all kinds of problems with this. 
Biggest problem is that Ubuntu 6.10 won't install, but there seem to be others: no DVD Live disk seems to boot (not Ubuntu, not Suse, not Knoppix), other distros do not run (Knoppix CD aborts).

The only stable distro that seems to work is OpenSuse 10.2 so far.
I also could install Ubuntu Feisty from Jan. 30th (though there were problems and crashes with the partition manager).

So my question is: would a SATA attached DVD writer work better here? 
I am prepared to shell out the Euros if it is *known* and to a certain extend guaranteed to work.

---

### Post by hal10000 on 2007-01-31
PATA DVD devices should usually work and it may be not necessary to plug in a sata drive.
It is very unlikely that all these cd's/dvd's should be damaged.

First look into your BIOS to see if it is possibly deactivated as a boot device.
THen, make sure your cable and jumper settings (master/slave/cableselect) on the dvd are correct.
Can you boot from another cd/dvd (e.g. your windows boot cd)?

---

### Post by kyphi on 2007-02-05
Same problem for me using the DG965WH board.  None of the live distros would boot.
I solved the problem by connecting one of the two DVD writers to one of the SATA ports.

You can buy an IDE to SATA adapter that plugs into the back of the CD or DVD writer.  It comes complete with SATA cable but you need a spare small power connector.  Most likely your powersupply will have that one available.
The cost for me was $28 (Australian).

This did not work for the second DVD writer.

---


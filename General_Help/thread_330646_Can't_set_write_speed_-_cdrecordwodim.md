---
title: "Can't set write speed - cdrecord/wodim"
date: 2007-01-03
forum: General Help
---

### Post by bmt on 2007-01-03
I'm trying to burn an .iso image to CD, but I can only make coasters. :o 

Using GnomeBaker or k3b, or command line, I can't reduce the burn speed to anything less than maximum.  GBaker has the burn speed greyed out (can't change it) and although k3b allows changes to be made (and passes them to wodim), the burn speed is still at maximum.  Setting a burn speed in command line options has no effect on the drive, even setting speed=0 (which should force minimum burn speed).

Any suggestions?  Reading through various stuff on cdrecord and wodim, I wonder if I should specify a driver to be used, rather than accepting the default mmc_cdr.

All this is happening on Dapper with Artec WRR 52Z (ide).

Resolved: All is working correctly after rebooting -- no idea what caused it.

---

### Post by wpshooter on 2007-01-03
Have you checked to see that your CD-Drive has the latest and greatest firmware installed ?

---

### Post by bmt on 2007-01-03
Yes, latest (only) firmware is installed.

---

### Post by digbysellers on 2007-01-11
I believe I may have this same problem. 
I have the "BYX2" firmware for Sony "DRU-710a".
 - Which succesfully burns at lower speeds in Nero in Windows XP. 

This seems to happen all the time for me in Ubuntu Dapper though, 
thus rebooting does not resolve the issue.

---

### Post by digbysellers on 2007-01-21
Updated to BYX5 firmware, no change. Booting back in to XP to use Nero is a real drag.

---

### Post by Pigeon. on 2008-01-13
> **bmt said:**
> Setting a burn speed in command line options has no effect on the drive, even setting speed=0 (which should force minimum burn speed).

I have a similar problem with a Sony DVD-RW DRU-810A when burning audio CDs.

At present the minimum speed possible through the GUI for audio CDs is 12x, (Sony DVD-RW DRU-810A) but this is less than ideal, because (a) it is better to burn audio CDs as slowly as possible to avoid hi-fi CD players complaining, and (b) the box concerned is a 450MHz PII and if the audio source file is compressed it can only just keep up.

From the command line, setting speed=1 on the command line results in wodim using speed=12.  Setting speed=0 results in it using the MAXIMUM speed, ie. speed=40, which is useless...

I can't update the firmware because the useless shower at Sony only provide a firmware updater for Windoze :(

---


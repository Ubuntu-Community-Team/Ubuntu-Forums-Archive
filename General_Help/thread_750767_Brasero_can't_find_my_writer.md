---
title: "Brasero can't find my writer"
date: 2008-04-09
forum: General Help
---

### Post by heartburnkid on 2008-04-09
OK, I'm trying to burn an audio CD using Brasero, and it can't find my DVD writer at all.  Once I hit the Burn button, the only option under "Select a drive to write to" is File image.  The writer is a Lite-On SHM-165H6S.  I haven't had any problems reading from it, but it does not seem to see it as a writer.

Running it under the terminal, the only error message that comes up is this (which seems unrelated):

```
(brasero:14362): Pango-CRITICAL **: pango_layout_set_markup_with_accel: assertion `markup != NULL' failed

```

I ran a cdrecord -checkdrive, to make sure that it is visible as a writer, and here's what I got:

```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
No target specified, trying to find one...
Using dev=1001,0,0.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'DVDRW SHM-165H6S'
Revision       : 'HS0D'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP

```

I assume that this means that the drive is set up properly.  So where do I go from here?

---

### Post by heartburnkid on 2008-04-10
Bumpity-bump-bump

---

### Post by plucky on 2008-04-10
From a terminal

```
 sudo lshw -class disk -class storage
```

and post output.

Can you try other Cd burners like K3B or Gnomebaker?

Good Luck

---

### Post by heartburnkid on 2008-04-10
You know, I was going to do that as soon as I sat down on my own computer today, but then I decided, "Hey, let's try Brasero again", and it works now. O_O.

I dunno, maybe it's because I restarted from hibernation yesterday, whereas today I started up from a cold boot... still, I guess I can't really do much in the way of troubleshooting now.  I'll post if it recurs.

---


---
title: "weird 30-second pause during boot, might have to do with floppy"
date: 2007-07-14
forum: General Help
---

### Post by shuffdog on 2007-07-14
Hmm.. so for awhile I've taken for granted that during bootup, the progress bar would pause at the start for about 30s, and today I decided I would find out why.

I was able to get as far as finding out, that dmesg shows this message taking up 30s of time:
[FONT="Courier New"]FDC 0 is a post-1991 82077[/FONT]
before moving on.

Any idea what this does / how to make it take half a second or something?

---

### Post by shuffdog on 2007-07-14
here is my boot chart.  I rebooted and it paused 30s at a different spot - but always not far after this displays:
[FONT="Courier New"]scsi1 : ata_piix[/FONT]

Would this have anything to do with that 'scsi eh 1' process, i wonder, or even that zombie 'sleep' process started by busybox?  Sigh.  Just guessing at this point.

---


---
title: "[SOLVED] Way to wipe a hard drive?"
date: 2008-06-03
forum: General Help
---

### Post by filligree on 2008-06-03
I was wondering recently if reformatting a hard drive, for example from ntfs to ext3 and then back to ntfs, has the same effect as messing about with drive wiping software?  I'm looking to compact the number of drives and computers I have down to a reasonable number of units, and hopefully to either sell off or donate the remaining hardware.  Obviously, I want to make sure none of my personal data is accessible once the drives have been wiped, and I thought that this might work.

Does anyone have any comments/experiences of this?

Alternatively, can anyone recommend any drive wiping software that runs in Ubuntu 8.04?

---

### Post by bigken on 2008-06-03
your data would still be there but you dont have run ubuntu to wipe the drives as most drive cleaning software is dos based im sure if you google about you will find a free software to wipe your drives

[http://dban.sourceforge.net](http://dban.sourceforge.net) this might help

---

### Post by Lord Xeb on 2008-06-03
Try this command

```
# shred -vfz -n ? (drive)
```

Were the "?" is, put the number of times you wan to shre the drive, then for were "(drive)" is, put the drive that you want to shred. Once your done, reformat you are good to go. Or just keep the drive in its raw state (since everything will be overwritten in zeros).

---

### Post by lisati on 2008-06-03
One machine I used many years ago had a "low level format" option but (adjectives deleted) if I can remember how it was done!

If you go with the old DOS "Format" command make sure that you DON'T use a "Quick" format by itself - the data will still be accessible to knowledgable people.

---

### Post by filligree on 2008-06-25
Thanks for all of those, I've been asked to wipe a couple of older drives by a friend, and I wanted to know if this option would work.  I shall try out the shred command, as that would cover all options.

---

### Post by brons2 on 2008-06-25
I use DBAN to wipe drives, it's a floppy bootable linux kernel.  (CD .iso also available)  You can chose the mathmetical pattern and number of passes.  Our standard is the DoD-5220.1 with 7 passes, which takes a long time.  The DoD short is probably ok for most folks.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---


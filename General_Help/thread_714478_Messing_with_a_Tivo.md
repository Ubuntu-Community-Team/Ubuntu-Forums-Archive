---
title: "Messing with a Tivo"
date: 2008-03-03
forum: General Help
---

### Post by skydiver|goose on 2008-03-03
So I work at RadioShack, and single tuner Tivo's has discoed (discontinued) down to $9.97, My store has 3 of them and my boss told me if I could figure out how to turn one of them into a DVR so that he could transfer all his videos from his PC to the tivo hard drive, he'd give me one for free to do the same with. I started by opening up the housing and pulling the hard drive, which I then plugged into a hard drive enclosure so I could plug in into my laptop via USB. What do I do from here?

---

### Post by antmenj on 2008-03-03
A few ideas:

Put the HDD back in the tivo and record something of air then try the same as above to see what format it writes to the drive in perhaps.

Install the drive in a desktop and try gparted so you can get an idea how it formats the drive maybe.

That may be a starting point.

My 2c

---

### Post by skydiver|goose on 2008-03-04
I'm using a Mad Dog Mega Vault 3.5" Hard Drive Enclosure on the HDD which uses a USB 2.0 A-B cable to go from the enclosure to my laptop; however, my laptop won't read the HDD as a storage device. I think it's a driver issue. Any idea how I can get past this?

---

### Post by skydiver|goose on 2008-03-04
here's a link to the enclosure I'm using:

[http://www.radioshack.com/product/index.jsp?productId=2407263&cp](http://www.radioshack.com/product/index.jsp?productId=2407263&cp)

---

### Post by antmenj on 2008-03-05
Ok you got me curious here so I grabed the hard drive out of my old Strong PVR and cabled it up as master on my desktop PC (also tryed cable select as thats whats used in the PVR).  Booted a puppy live CD.  Drive not recognized.

Did the same with a systemrescuCD. Started GParted.  It says the whole drive is empty but it has a good few hours of recordings on it.

I conclude the PVR uses an unknown format eg not fat(x), not NTFS, not ext2, not ext3, etc

Try a drive out of a computer in your USB case to see if that mounts.  A friend came in one day with one of them and we pluged it in and it just came up as a icon on the ubuntu desktop.

---


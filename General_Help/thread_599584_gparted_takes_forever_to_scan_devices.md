---
title: "gparted takes forever to scan devices"
date: 2007-11-01
forum: General Help
---

### Post by notatoad on 2007-11-01
when i load gparted, it takes about 5 minutes to scan all my hardware.  on fiesty it used to take ~15seconds.  anybody know how to fix this?

---

### Post by Pumalite on 2007-11-01
Check your BIOS. Make sure all is set OK.

---

### Post by Yfrwlf on 2007-11-07
It may be an issue only related to SATA drives.  In Gutsy, GParted finds all drives immediately on my IDE machine, but on all machines with SATA it takes about 5 minutes or so to scan.  I'd imagine they are probably aware of the bug at this point...

QTParted is much faster at scanning than GParted is (if you have SATA drives), no clue why,  but I couldn't find much discussion about this bug around the net, tho I'll keep looking.

---

### Post by Yfrwlf on 2007-11-07
Update: We seem to have found the solution.  Disabling the floppy drive in the BIOS fixed this issue.  What I read is that when you have a floppy drive enabled and connected, this problem won't happen, but if there is no floppy connected but it's still enabled in the BIOS, scanning will take forever.  Disableing the floppy in the BIOS on one computer fixed the problem.  Haven't tried it elsewhere but at this point that seems to be the patch solution for this bug!

---

### Post by Holonet on 2008-01-27
I have had this issue as well, and I have a floppy connected.  I'm running a Gigabyte M55SLI board, AMD 4200+ Dual Core, 2 GB of RAM.  I haven't tried disabling the floppy yet, but thought it should be known that it can happen with the floppy connected as well.

---

### Post by BuffaloX on 2008-01-27
I use SATA only, 2 harddrives one DVD/RW
Gparted scans for less than 5 secs.

1:
I use NVIDIA chipset SATA for my drives, maybe if you have choice of controllers it would help to 
swap your drives to the other controller.
2:
Check if everything is detected corretly, (no drives or partitions missing or unidentified after scan)
3
Make sure you have SMART enabled, and follow the BIOS prompts to see if there are any SMART error reports.
4
Check web if there should be general problems with your model and make of controller.

---

### Post by Holonet on 2008-01-27
Yep, well GParted scans in about 8 seconds for me, that's one 250 GB drive, if I disable the floppy in the BIOS.  So I'd say it's confirmed that has something to do with the problem, but like I said, I do have a floppy, and I've used it before in Windows, so the bug will have to be addressed from that perspective.

---

### Post by BuffaloX on 2008-01-27
Thats consistent,
I don't use floppies, and have it disabled.
If I should need a diskettedrive, I have an external USB drive I use, which is stored in some box in some closet somewhere.

---

### Post by onesojourner on 2008-01-27
wow I am glad I found this thread. It took me 15 minutes to load up gparted before. now it takes 15 seconds.

---

### Post by BluntBox on 2008-03-17
Thank you muchly for the Floppy drive solution. Gparted was driving me insane with its 5min+ device scans. 5 seconds tops now.

I love these forums, there is an answer for everything!

---


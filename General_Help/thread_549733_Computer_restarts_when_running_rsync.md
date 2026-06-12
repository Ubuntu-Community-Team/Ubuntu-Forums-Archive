---
title: "Computer restarts when running rsync"
date: 2007-09-12
forum: General Help
---

### Post by JinxAu on 2007-09-12
Gday everyone,

Just thought I would ask on the forums here to see if anyone had any ideas as to why a Ubuntu Feisty (7.04) 32bit Desktop would reboot everytime rsync is run on it?

It's got me a bit confused, as I have checked the RAM and the IDE HDD (hda) and they all report that they are ok (used memtest and Hitachi Disk check).

Have also replaced the PSU with another 400W PSU. Specifications as follows:
- AMD 3500 939 processor
- 2 x 512meg DDR1
- Uli onboard network card
- AGP Nvidia 6200 Graphics card (dual monitors)
- 1x 40gig Seagate IDE HDD (hda)
- 2x 80gig Western Digital SATA HDD(s) (md0)

Not sure on the brand of the Mainboard (forget the name)... will try and track that down.

The two SATA drives are put together to form a RAID1 EXT3 /home partition.

The system is quite stable until you try running an rsync backup... I am going to do some tests as to whether it is dying when backing up the system drive (hda) or the /home parition (md0). I suspect it is not rsync that is causing the drama, more the fact that it is putting load on the system and hence causing it to fall over.

Any advise would be appreciated.

Cya round
Jinx

---

### Post by HermanAB on 2007-09-13
I have esperienced rsync causing restarts when transferring directory trees with really large numbers of files.  The solution is to throttle rsync.  It has a setting that you can use to reduce the maximum bandwidth usage.  Somehow that allows rsync to keep going.  

I suspect that reducing the bandwidth setting, causes it to run with less packets outstanding, so the error retries have time to complete, otherwise error packets build up and it runs out of RAM and crashes or something like that.

'Hope that helps!

Herman

---

### Post by JinxAu on 2007-09-13
Thanks for the feedback Herman... will try throttling.

I ran a test to see when it actually reboots. It appears it reboots when trying to backup the /home directory... which is the SATA RAID1 Mirror (md1... md0 is the swap. I suspect when you say is correct when it seems to be running out of system resources.

Might also be a bit more load on the system from the RAID1 (although, it's reading from it, not writing to it). Though, because the Swap partition is a RAID1 across these two drives, you could say there would be a few writes happening whilst rsync does it's job... maybe that's what is causing the problem.

Will let you know how I go.

Cya round
Jinx

---

### Post by JinxAu on 2007-09-16
Well, the problem appears to have been with having a swap on /dev/md0... have since put it back to /dev/hda5 (on IDE drive)... doesn't seem to be rebooting anymore.

Thanks for the help.

Cya round
Jinx

---

### Post by JinxAu on 2007-09-20
Gday everyone,

This turned out to be a hardware fault, not software. Apparently my ASRock Mainboard doesn't like running 1T timings for the CPU. I am not quite sure what this means, but ended up turning this to 2T and Cool'N'Quite off in the BIOS... hasn't rebooted since... *knock on wood*.

Cya round
Jinx

---


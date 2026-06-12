---
title: "boot up mystery"
date: 2008-03-08
forum: General Help
---

### Post by bennyda on 2008-03-08
Hi all,

I am currently using Feisty (not yet sure if I should upgrade to Gutsy), on a dual boot laptop with Windows XP Home.

In order to be able to read AND write to my NTFS partitions, I installed ntfs-3g. Everything works perfectly, however, now during boot-up the Ubuntu status bar stalls at around two thirds the way for around 2 minutes before continuing. After that everything is A-OK.

Any ideas as to this mystery stall?????

---

### Post by Shazaam on 2008-03-08
Hmm. Anything in dmesg (var/log/dmesg)? Poke around in the log files and see if you can find anything.

---

### Post by bennyda on 2008-03-09
shazaam,

thanks for your reply.

i checked the logs but can't seem to narrow down the issue. in dmesg i found the following which raises a question:

[    4.908000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.908000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    4.976000] sd 0:0:0:0: Attached scsi disk sda
[    4.980000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.980000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.996000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.996000] Uniform CD-ROM driver Revision: 3.20
[    4.996000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.280000] Attempting manual resume
[   [B] 5.280000] swsusp: Resume From Partition 8:5
[    5.280000] PM: Checking swsusp image.
[    5.280000] PM: Resume from disk failed.[/B]
[    5.316000] kjournald starting.  Commit interval 5 seconds

note the lines in bold. do you think the stall could be something to do with that? i don't have any problems suspending to disk though. it works just fine.

i observed the stall (approx. 65 sec) occurring after i had installed ntfs-3g. is there any way i can stop that from loading? just to check if that's causing this?

not that i have any problems otherwise. everything works great (fingers crossed).

by the way, i also have nfs and samba installed but stopping those didn't solve the issue.

---


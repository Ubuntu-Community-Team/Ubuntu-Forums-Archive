---
title: "ddrescue regenerated mapfile for resume -- missing non-trimmed blocks?"
date: 2022-02-16
forum: General Help
---

### Post by zardano on 2022-02-16
I started ddrescue to recover a failing 2TB WD drive from my NAS.  Although I specified a logfile, unfortunately I was running ubuntu in trial mode from a bootable flash drive and did not write the logfile to a separately-mounted drive, so when the power went out around 11%, I discovered that I lost my logfile. ](*,)

Under chapter 14 of the manual, the generate mode looked like it might work, so I ran:
```
ddrescue --generate-mode infile outfile mapfile
```

The drive I am recovering to is a brand new drive, so I was hopeful that it would work since there was no old data present on the drive.

I then used the generated mapfile to run ddrescue again with:
```
ddrescue -f -n -r1 /dev/sda /dev/sdb /tmp/ddrescue.log
```

(I'm running Ubuntu now installed to an ssd).  
This appears to have worked for the most part, as the recovery process restarted around the 11.5% mark, right where it left off.
My concern though is that before the crash, ddrescue had identified one read error, and had shown about 20MB of non-trimmed blocks, but on starting the process with the new mapfile, there were 0 read errors marked and 0 non-trimmed blocks.  
Now after running for 8 hours, it shows 2 errors and 29696B of non-trimmed blocks, but I'm assuming these are new read errors because ddrescue isn't looking at the old data portions that were already marked as rescued.

Will ddrescue discover the original read error on a subsequent pass, or is that one gone for good, and the only way to find and re-try those blocks would be to start everything over from scratch with a new mapfile?

I'm wanting to recover as much as possible from the old drive, if not everything, so I'm willing to start over if necessary.

Thanks for any help on this.

---


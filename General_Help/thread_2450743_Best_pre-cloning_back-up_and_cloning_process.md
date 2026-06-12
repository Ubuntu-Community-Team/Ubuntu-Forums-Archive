---
title: "Best pre-cloning back-up and cloning process??"
date: 2020-09-19
forum: General Help
---

### Post by goggins on 2020-09-19
I have an older Dell with a 1T HDD running ubuntu 20.04 LTS 64 bit, under 200 gig in use, issues with machine so I intend to upgrade to a Dell XP with 512 gig SSD and 1 T HDD which will be delivered with Windows installed. My desire is to do a fresh install to the new machine and then transfer over everything necessary to preserve all data and settings PLUS some legacy software running under wine and at least one custom install not using apt (DroidCam). I hope to do the new install not only to SSD, but also to HDD, so HDD can be emergency recovery drive, hence bootable and all that.

I have a pair of long idle externals - an old seagate 250 GIG and a somewhat newer WD 1,000 Gig.  The new machine will have different drivers and such for video card, sound card, bluetooth & wifi etc, which will hopefully be installed at ubuntu install, but I would like to copy pretty much everything else over as is, except bad tracks and such, and really don't know what to grab and where to start short of some sort of cp* , which doesn't help with the restore and I'd really prefer to back up but then, if possible go direct machine to machine and leave the externals out of it.

Any advice?

---

### Post by CelticWarrior on 2020-09-19
The default backup tool and an external drive is pretty much all you need.

---

### Post by goggins on 2020-09-19
IIRC, that gives me a tar, and if I'm stuck with unpacking it to the new hardware I'll overwrite the new drivers and such, won't I?

---

### Post by CelticWarrior on 2020-09-19
In the new one you use the same tool to recover, it's quite simple.

---

### Post by goggins on 2020-09-19
Thanks.

---

### Post by TheFu on 2020-09-19
Use any file-based backup method you like, then selectively install the stuff you need restored.
Tar was designed for 50MB stuff, not 50GB. Use a real backup tool, not something like ZIP.

There are lots and lots of threads about backups in these forums.  Find one of those that makes sense to you and do that method.  Expect the restore to take a few attempts to get correct, until you get good at it.  Once you hve that down, it is knowledge for life.

---

### Post by goggins on 2020-09-19
The back-up I found is Deja Dup. Is it recursive? If I back up home, do I get everything?

---

### Post by HermanAB on 2020-09-20
Read this before using DejaDup:
[https://kitson-consulting.co.uk/blog/how-recover-corrupt-deja-dup-backup-and-set-alternative](https://kitson-consulting.co.uk/blog/how-recover-corrupt-deja-dup-backup-and-set-alternative)

---

### Post by TheFu on 2020-09-20
> **goggins said:**
> The back-up I found is Deja Dup. Is it recursive? If I back up home, do I get everything?

Be careful using DejaDup.  If you do choose that, make certain you understand how it works, how it doesn't work, and have tested the restore.  Best to test the restore by taking your backup disk to a friend's place and see what you forgot.  For example, people often include the decryption keys inside their backups, but don't have any way to unlock those backups to get to the decryption key.  Chicken-egg problems.  

And until you actually test, you'll not know the others.  Took me about 5 attempts to ensure my backup methods worked.  I've been improving those for about a decade, so lots of little other things are part of my backup data now.  For example, I capture the disk layouts now, updated daily, versioned, included in my backups.  Disk layouts include 
sfdisk output, lvm pvs, vgs, lvs, df -hT, so I know what I had before.  It would be unusual for me to actually re-create the old layout during recovery. I always tweak the new layout slightly - more in /boot/ is common.  Sometimes I need to tweak the size of the swap or include a separate area for /var/ that I didn't think was important 4-6 yrs earlier.  My 20.04 install has been tweaked twice, since the way things get added via snaps totally screwed over my allocations.

Plus, having excellent backups means that pretty much any issue can be solved in about 30-45 minutes. Imagine having some problem that you've spent 4 hrs trying to fix.  Never again. After 30 minutes, I just pave over everything and restore from backups taken last night or the day before or 16 days ago or 34 or 73 days ago.  Efficient, versioned, backups can change your computing life completely and there really isn't THAT much storage needed if done well.   My 20.04 desktop backups, regulus:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Sep 20 01:15:03 2020         5.38 GB           5.38 GB   (current mirror)
Sat Sep 19 01:15:04 2020         18.5 MB           5.40 GB
....
Thu Jun 25 01:15:34 2020         2.25 MB           5.81 GB
Wed Jun 24 01:15:03 2020         2.87 MB           5.81 GB
Tue Jun 23 01:15:03 2020         3.53 MB           5.82 GB
```

So for 90 days of daily, automatic, versioned, backups, I need less than 6G of storage.  I have a really hard time understanding excuses from people who claim they don't have storage for this stuff.  How can they NOT?
As you can see, I'm selective about getting only the things needed in my backups.  I exclude most of the OS, all cached stuff, all temporary files, and anything that can be reinstalled trivially.  I used to backup more stuff when I wasn't certain.  When it was time to move from 16.04 to 20.04 for my desktop, I brought the data and settings from that 16.04 system over, after the fresh, minimal, 20.04 install was done.

Backups aren't hard. They do take practice. The more you practice anything, the better you will become.  The most important part of the testing is the restore attempts.  I don't know of any substitute for practicing restores.

---


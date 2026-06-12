---
title: "Repeating Error to superblock"
date: 2013-02-23
forum: General Help
---

### Post by djuke04 on 2013-02-23
I've searched a lot for solutions to this and found nothing that worked or quite matched my symptoms.  

I've had crashes and problems for YEARS with the same symptoms.  Sometimes it happens a few times in one day, then it could wait a week or more with no restarts and no problems.  Lately its everytime the computer runs.  I noticed a couple years ago that this would happen almost immediately if I completely close the case by putting it's side on it and the screws in the back that hold it on.  I can't make a lick of sense out of that...  the side piece touches absolutely nothing hardware wise, not even a case closed switch.

The symptoms were pretty much the same in every version of Ubuntu I've used since 9.04 or so, but the error messages and numbers have changed a bit (didn't used to use EXT4 for instance).

Nothing will launch, the icons turn into pages with a red x on them and the system is unresponsive.  At this point, it won't even shut down or restart usually.  I always have to force the power off by toggling the power supply or holding the power button for until it shuts off.  Then I restart, go into recovery mode and run an fsck where it says:

/dev/sda1: Superblock last mount time is in the future.
                  (by less than a day, probably due to the hardware clock being incorrectly set)  FIXED
/dev/sda1: 513023/3662848 files (0.2% non-contiguous), 4153871/14648064 blocks

Finished, please press ENTER

____________________________

Everything restarts normally, and an unknown amount of time goes by until the error repeats and work is lost, wife is frustrated, patience goes out the window...

If it is ever responsive enough to "shutdown," it never actually finishes shutting down, but just says:

EXT4-fs (sda1): previous I/O error to superblock detected
EXT4-fs error (device sda1): ext4_find_entry:935: inode #1440812
comm sh: reading directory lblock 0



So to try and work with this I have:

*used a different hard drive - complete fresh install, new solid state drive, start over
*changed motherboards to a newer fancier model (that was some time ago, two years back maybe)
*updated my BIOS to most current version
*Set BIOS to both optimized and fail-safe defaults (errors are the same regardless)


Please somebody help me.... 


What else can I do to diagnose this? I'm definitely out of my Linux league here.  Thank you for reading and thank you SO much in advance for your suggestions and advice.  I really really appreciate it!

---

### Post by schragge on 2013-02-23
Please post the output of 
```

cat /etc/adjtime

```

Also have a look at
```

more /usr/share/doc/util-linux/README.Debian.hwclock

``` This document explains how hardware clock works.

---

### Post by djuke04 on 2013-02-23
max@HTPC:~$ cat /etc/adjtime
0.0 0 0.0
max@HTPC:~$


I'm looking at that second part you posted right now.  Holy cow fast response thanks!

---

### Post by djuke04 on 2013-02-26
So I changed my memory setting in my BIOS not to accelerate performance of the RAM, and I thought oddly enough that fixed it because it worked for a couple days.  Just now however, it has frozen again and now it will no longer recognize one of my two storage SATA drives that automatically mount from fstab.  I can't get them to mount at all, but the BIOS sees them, linux just hates me.

Windows doesn't have a problem with my hardware and doesn't freeze or anything, but I prefer not windows.  

Does anybody else have any other suggestions?

---


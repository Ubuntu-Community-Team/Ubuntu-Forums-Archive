---
title: "Lots of failures. Need help, last resort = reformat"
date: 2007-10-20
forum: General Help
---

### Post by t-bone510 on 2007-10-20
Hey guys. I've lurked a while and I've seen how helpful this place is, so I decided to post here. help.


Running Gutsy


Ok, so all was well, i was in my ubuntu partition.

Steam was running and downloading day of defeat, i was using WINE. (problem #1 i presume)

Ok, so. Randomly

Everything slowly turns  to black and white, and i cant do anything, the system is unresponsive....

I held my power button for 10 secs, booted back into linux, all is good. Log in, then, i get the welcome  music, then it turns black and i get a message that says "your session lasted less than 10 seconds" and something about ran out of disk space? I didn't run out... i had 10 GB left and steam was DLing a 6GB file.

So, i reboot again, choose ubuntu normal.

Then, it starts a disk check (fsck), all goes well until it gets to 90%. Then it says check failed. Starts a terminal, but many commands are disabled. Im in my windows partition now.

 i tried to boot into recovery mode:
I booted in, and it just started another disk check

failed at 90 percent

then it said that the volume will be mounted in read only mode. it gave my a thing similar to terminal.

--------------------------------------------------trying to boot again

some stuff scrolled by faster than I could get it, cant scroll back up.

heres what i caught

/dev/sda4/ contains errors: CHECK FORCED

starts the check, fails at 89-90% (again) 



/dev/sda4/
Unattached inode 1436169

/dev/sda4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e., without -a or -p options)
fsck died with exit status 4
FAIL (big red letters)
*An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.

root@travis-desktop:~#



I ran fsck manually, it did some things, then reached "connecting lost and found" or something like that

It stuck at that point for 9 hours, so i rebooted again and the same stuff again.

I really don't know what to do. I tried using windows to scan the volume for errors but to no avail.

Any ideas?

---

### Post by t-bone510 on 2007-10-20
Tried it a few more times, should I just put in my 7.04 Live cd and be done with it? Or is there a fix...?

---


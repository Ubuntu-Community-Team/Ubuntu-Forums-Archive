---
title: "Shutdown issue"
date: 2008-05-11
forum: General Help
---

### Post by dksau on 2008-05-11
Okay this might be complicated, its going to sound like a logic problem.  I have two computers with Ubuntu 8.04.  The computer that I was dual booting with Windows XP pro and Ubuntu 8.04 (A) had a motherboard problem and wouldn't boot so I ordered a bare bones kit which has only one IDE. I had two hard drives and a CD/DVD RW. Since I only had one hard drive in the Ubuntu only computer(B) which has two IDEs I moved the two hard drives from A to B and the single hard drive from B to A.  When the two hard drives were in A with the old board there were no jumpers on either hard drive and there aren't any now either.  Before the hard drives were moved A would not shut down when quitting Ubuntu 8.04 (at least an any reasonable amount of time).  After moving the two hard drives to B Ubuntu will not boot normally but will boot in recovery mode.  How can I cure this problem?:confused:

---

### Post by frodon on 2008-05-11
Putting the jumpers on your drive in correct position, cable select on both is the best setting IMO).
To know how to put the jumper refer to your drive manufacturer specification, on some new drive there's a small pattern next to the jumper area.

---

### Post by dksau on 2008-05-11
I bought one of the drives to replace the other since it is old while only running windows. During the process of that time a new copy of windows was installed on the old drive.  Luckily I was able to recover most of my old data. The new drive didn't contain any instructions and has no diagram to indicate how to configure it so I just tried something to get the computer running out of frustration.  It came wrapped in a conventional static resistant plastic envelope and I never heard of the brand but I wanted it because it was small enough.  It appears that the two hdd were treated as one with 2 partions except that each contains a ext3 and the windows type other than FAT32 which I can't remember the name of right now.  I find this by examining each with gparted.

---

### Post by dksau on 2008-05-11
frodon

 Thanks for your help.  I know just enough to get into real trouble with computers.  I started when I had to write all of my own programing in basic but now I don't know a language to write in or I could cure almost anything.  If I have a recipe I can tackle a lot of problems.  I get to experimenting at times because I have three computers I can play with.:)

---

### Post by dksau on 2008-05-11
frodon

I looked at gparted again.  One drive has about 7 partitions adding up to the published capacity of the hard drive.  My problem now has become a boot up problem.  I can only boot to ubuntu in recovery mode.  When I changed the drives the monitor I was running before was at a high screen resolution.  The generic CRT I have it on now can normally only handle 800 X 600 so I'm booting but get a warning that there is no video signal from the monitor.  Is there a command for this I can use to fix it with from terminal in recovery mode?

---


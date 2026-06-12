---
title: "boot hangs at fsck"
date: 2006-11-06
forum: General Help
---

### Post by Choad on 2006-11-06
using xubuntu edgy, the boot will now hang at the filesystem check. it always used to get a little stuck there, as there are some wierd errors going on with one of my fat32 partitions, however that was just informing me of the error and getting on with it after a few seconds

now the boot just switches to text mode and says "fsck" as its checking one of my file systems, and it obviously uses alot of cpu cycles (bug in the programming?) because it causes the fan to step up to the highest setting - however there is no hard disk access going on (the light doesnt flash)

now this totally sucks, i cant get in in recovery mode either, so i cant fix the filesystem

honestly what kind of a desktop OS breaks it's self in this way? if i didnt dual boot windows i would be totally screwed

---

### Post by Amby on 2006-11-07
I've got exactly the same problem, but I don't have any Windows partitions, just two reiserfs ones. I already tried some of the advice that were about similar situations. Actually I could get the boot up work _once_ after changing the sixth field (replaced 2 with 0) for the reiserfs partitions in fstab, but after a reboot it got stuck again. Now I can't do the same fix twice so I'm kinda stuck. 

When I found out someone other than me has experienced the same I just had to create myself an account here just to inform that it isn't an isolated incident.

This needs to be fixed ASAP.

- J -

---

### Post by Amby on 2006-11-07
Also, they say this has been fixed, but I still can't seem to find the fix. 

[http://ubuntuforums.org/showthread.php?t=269379&highlight=fsck](http://ubuntuforums.org/showthread.php?t=269379&highlight=fsck)

---

### Post by Choad on 2006-11-07
ok well i fixed it myself... im not quie sure of the reasons why it wasnt workingon boot, but i just popped in the live disk and ran fsck on each partition.

i think a nero6 temporary cache file was confusing dosfsk, but i've got no idea why it was sticking on e2fsk before. oh well. i also disabled checking the windows drives for errors on startup by editing /etc/fstab/ :)

---

### Post by Lusse on 2006-12-01
I have the same error but if I wait for a long time Ubuntu starts!

---

### Post by cesium62 on 2008-01-26
Who's the moron who thought that a 20 minute boot was a good idea?  fsck should be a continuous background process, not a 20 minute waste of time once every 20 or 30 boots.  This has to be the stupidest damned feature that has ever been implemented in a computer system.

---

### Post by PmDematagoda on 2008-01-26
> **cesium62 said:**
> Who's the moron who thought that a 20 minute boot was a good idea?  fsck should be a continuous background process, not a 20 minute waste of time once every 20 or 30 boots.  This has to be the stupidest damned feature that has ever been implemented in a computer system.

You do know that fsck is supposed to be executed on unmounted drives when you said that, don't you? If you execute fsck on a mounted drive then it can cause data corruption, so imagine what would happen if you were doing an fsck check on the root partition while you were moving a file or any other tasks that concern using the hard drive(and there are a lot even if the OS is just doing nothing).

---

### Post by cesium62 on 2008-01-26
You're being overly literal.  Think outside the box.  fsck verifies the integrity of the filesystem.  Techniques exist and can be invented to allow the integrity of the file system to be verified while the disk is being used.

Having to wait 20 minutes for a system to boot is just absurd.  Having the boot appear to hang for multiple minutes becase the process didn't figure out how to print out some sort of "i'm making forward progress message" at least once every 10 seconds compounds the absurdity.

---


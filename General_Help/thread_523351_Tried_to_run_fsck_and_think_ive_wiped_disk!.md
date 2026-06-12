---
title: "Tried to run fsck and think ive wiped disk!"
date: 2007-08-11
forum: General Help
---

### Post by mental_drummer on 2007-08-11
Hello every one,

heres a blow by blow account of my screw up

Linux and windows dual booting on my primary hard drive and a linux home directory on the salve. I booted in recovery mode and ran fsck on the slave but it seemed to have problems it couldnt resolve. I then ran badblocks on the drive to see if that would work. That seemed to freeze or not do much so I ctrl+c it and gave up and rebooted.

Now the hard disk seems to be wiped! When i look at it in gparted it says its completely blank. I cant believe the data is actually gone seeing as the comp wasnt thinking loads or anything. I think the partition is just screwed somehow.

Any help would be very much appriciated.
Thanks guys

---

### Post by yorkie on 2007-08-11
when you rebooted was it with livecd or normal boot if it was a normal boot the data is still on your h/d

---

### Post by mental_drummer on 2007-08-12
it was a normal boot but thats because th OS is on my primary hard drive. My main home directory is on the slave. I cant log into the profile for that home directoy as it says it cant find the home directory. However I have another profile based on the primary disk that does work.

So I think that means it could be wiped?

---

### Post by kerry_s on 2007-08-12
yeah, i say you boned it. your not suppose to be able to run fsck on a mounted drive. sounds like you forced it some how.

---

### Post by mental_drummer on 2007-08-12
i unmounted it first

---


---
title: "lvm keeps crapping out"
date: 2013-11-01
forum: General Help
---

### Post by wt12 on 2013-11-01
I'm new to Ubuntu (and linux in general).  I'm attempting to setup a media server with 12.04.  I'm running into a stability issue... works sometimes, fails sometimes.  I have 4 drives.  1 SSD that the OS is on.  3 identical 2TB drives that I used LVM to group together as one 6TB drive, mounted to /mnt/bigdisk

I think I fudged through it OK because it worked... for awhile.  Then, as I was transferring a bunch of MP3 files, the transfer failed and the server was wholly unresponsive.  I rebooted it (power button) and it never came back on.  I grumble and moan as I haul my monitor and keyboard to it to so I can see what's going on... and its telling me my /mnt/bigdisk isn't available and I have to hit S to skip (wtf is it waiting for that for?  let me boot up and worry about it later!).  Fine, I skip.  I re-mount it.  reboot.. everything's fine... for awhile.  Today I'm editing mp3 tags on those files and at some point it gets extremely sluggish to respond.  Eventually crashing the program I'm using.  I SSH to the server and tell it to reboot... but it doesn't respond.  Hit the button again... haul my monitor and keyboard back over expecting to see the same message, but this time it won't even boot at all.  BIOS is extremely sluggish (very odd).  I unplug all drives and replug them, that solves the bios issue (weird, right?) and then again I see the "press S" message.


So what's going on?  I don't even know how to begin diagnosing this.

Thanks.

---


---
title: "Load testing"
date: 2007-06-16
forum: General Help
---

### Post by CrazyGuy123 on 2007-06-16
I've been trying to reproduce bugs some people have had with disk corruption.  I've set up a little test station, which will simulate a user using the system by starting ubuntu, opening a few web pages and programs, then rebooting and starting windows and starting a few programs, and then starting ubuntu again etc.

So far, It's started ubuntu and windows each flawlessly 500 times. (once every 2.5 mins)  That is good news for users as it shows there's no problem with using this long term.  It is however dissapointing for me as I havn't tracked down the cause of this bug.

My next step will be to add a hard reboot randomly every 4 or so bootups of each OS, and see if that impacts things.

If I can't get anything with that, I'll add more junk on both the ubuntu and windows disks, and make sure everythings a bit fragmented and retry the process.

The whole thing is being recorded so if at any point something fails, the system can be reverted to how it was at the previous boot, and the problem can be analysed.

I'll use this thread to post the results.

---

### Post by acowboydave on 2007-06-26
Hello, I hope I'm not posting in a wrong spot. Something on a reinstall happened to me and if may have an effect on install or reboot. Using test 4, on a reinstall I left Home Virtual Disk checked. Install went normal but after everything was finished I checked file system and instead of having 14.8 G in system I had 29.6 G. Home remained the same at 11.9 G. Could be a problem if one did not have the room.

---

### Post by ago on 2007-06-26
> **acowboydave said:**
> Hello, I hope I'm not posting in a wrong spot. Something on a reinstall happened to me and if may have an effect on install or reboot. Using test 4, on a reinstall I left Home Virtual Disk checked. Install went normal but after everything was finished I checked file system and instead of having 14.8 G in system I had 29.6 G. Home remained the same at 11.9 G. Could be a problem if one did not have the room.

The "room" is calculated automatically, when you backup home, by "installation size" we mean system+swap. If home is not backed up installationsize=system+home+swap.

---

### Post by acowboydave on 2007-06-26
Thanks for replying, my point or question, is my installation increased almost 15 G, from what I thought to install. If I didn't have the room would it not fail? And being a beginner I really wouldn't know why? I started out to only have 30 G and after the reinstall ended up with 41.5.

---


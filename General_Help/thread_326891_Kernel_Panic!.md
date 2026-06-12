---
title: "Kernel Panic?!"
date: 2006-12-28
forum: General Help
---

### Post by cgobble on 2006-12-28
OK, new guy here....please be gentle with me.  

I've run Dapper Drake on my AMD Athlon 600Mhz machine for about 3 months now.  I've used it for basic word processing, browsing, and music transfer.  I've done a little bit of terminal command stuff, not much though.  Yesterday I downloaded some games through Synaptic.  As I was shutting down a game, Scorched Earth 3d I believe, my computer locked up.  I tried a few things but couldn't get it to do anything.  I forced the computer to shut down by holding down the power button.  I know, bonehead move.  Now my computer will not boot.  I do not run a dual boot scenario.  I'm all Ubuntu.  I've tried to run the boot disk.  I've tried to "rescue a broken system".  I always get the same message...."Kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block(1,0)"  How can I fix this?  To complicate the matter, the fix needs to be simple enough for a newbie to tackle.  I do not have any files on the machine that I can't afford to lose.  Is there a reasonably simple way to just reinstall the OS.  I anxiously await your collective wisdom and advice.  Remember, please be gentle with me!

---

### Post by kidders on 2006-12-28
Yuk! Nasty error message.

Messages like these often occur as a result of a mistake made regenerating the bits of your system used during boot. Did you by any chance upgrade your kernel (or something related) after your previous reboot, but before your PC crashed? (Basically, I'm wondering if the crash really was the cause of this problem.)

Assuming for the moment that it *was* the cause, it is more than likely down to a filesystem corruption. I would recommend the following:

[LIST=1]
[*]Check your filesystems for errors ... hopefully there are errors.
[*]Erase your swap partition, particularly if you like to hibernate your PC.
[*]Reinstall your bootloader, just in case.
[/LIST]

All three steps may not be necessary, but between them, you should cover a *huge* range of possible problems. Try the following:

[LIST]
[*]Boot from any Linux CD.
[*]fsck all filesystems that were mounted at the time of the crash.
[*]Reboot and see if there's any change.
[*]If not, worry about items 2 & 3 on my list.
[/LIST]

**Edit:** If one of your filesystems *has* corrupted, my primary concern is the wellbeing of your personal data. After all, your Ubuntu system can be replaced, but you should think twice before performing any repairs on partitions that hold your /home. If in doubt, dump the partition somewhere, so you can try the repair again if it goes badly for some reason. Let me know if you feel like you want to do that.

---


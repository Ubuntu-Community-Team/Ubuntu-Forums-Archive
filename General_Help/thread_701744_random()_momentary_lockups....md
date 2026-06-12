---
title: "random(?) momentary lockups..."
date: 2008-02-19
forum: General Help
---

### Post by phrawzty on 2008-02-19
Hi all,

I am experiencing seemingly random *temporary* lockups on my freshly-installed Gusty HP dv9000 laptop.  I can still move the mouse pointer around, and any *sounds* that are playing will continue to play without any interruption; however, i cannot interact with the GUI, and any video playback will freeze.  After a short delay, the system will resume as normal.

Take, for example, playing an AVI in VLC.  The video will freeze for 3 or 4 seconds, but the sound will continue to play without delay.  When the system un-freezes, the video jumps ahead to the correct spot.  During a freeze, i can move the mouse pointer around, but clicking on things is pointless.

Oddly, when the system un-freezes, things that i clicked on during the freeze will activate.  This has lead me to believe that something to do with video or interface rendering is at fault, but honestly, i'm not sure how to continue diagnosing this issue.

Any help would be greatly appreciated.  Thank you!

---

### Post by BoeBoe on 2008-02-20
You can try look for any cpu hogging applications. Run 'top' from terminal console and see which apps is consuming your cpu.

---

### Post by phrawzty on 2008-02-20
Thank you for your reply, BoeBoe.

Unfortunately, while the system is stuck, i cannot open a terminal to check top, nor can i open the system monitor (as i cannot click on anything).  When the system un-sticks, and i'm able to launch the appropriate tool(s), there are no applications which appear to be consuming more resources than would be expected.

---

### Post by BoeBoe on 2008-02-21
Hi phrawzty,

Does the lockup happens only when running VLC, or during system idle ?

---

### Post by phrawzty on 2008-02-22
> **BoeBoe said:**
> Does the lockup happens only when running VLC, or during system idle ?

It is not possible to detect the lock up if i'm not active on the system (since it's a temporary pause, of course); however, i can confirm that the lock-ups occur whether VLC is running or not.  For example, right now i only have Firefox running, and i experienced two of the momentary pauses while typing this reply.

---

### Post by BoeBoe on 2008-02-25
Some lockups can be caused by faulty hardware as well. You might want to check your memory and harddrive. You can boot the Ubuntu installation CD to do this.

---

### Post by phrawzty on 2008-02-25
> **BoeBoe said:**
> Some lockups can be caused by faulty hardware as well. You might want to check your memory and harddrive. You can boot the Ubuntu installation CD to do this.

Thanks for the suggestion; i've checked the hardware using a number of tools, and found no faults whatsoever.  Moreover, the freezes do /not/ occur when using Windows, which further indicates it's a problem with Ubuntu.  Finally, i installed Fedora Core 8 over the weekend, and the freezes are nowhere to be found; this more or less validates where the fault lies, generally speaking.

Unfortunately, as far as this particular laptop is concerned, Ubuntu doesn't appear to be the right fit.  Oh well - thanks for trying to help anyways !

---


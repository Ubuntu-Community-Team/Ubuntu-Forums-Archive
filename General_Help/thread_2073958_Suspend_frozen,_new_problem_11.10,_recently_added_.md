---
title: "Suspend frozen, new problem 11.10, recently added Windows that's the only change"
date: 2012-10-20
forum: General Help
---

### Post by raequin on 2012-10-20
We have a Gateway T-6836 to which I recently added an NTFS partition and set up dual boot with Vista (that was fun).  Things were working like normal on Ubuntu (11.10) until yesterday.  Now it's freezing on suspend, or rather not waking up.  There's nothing but a black screen.

Two nights ago I made a lot of changes to Windows.  Could that be causing my problems with suspend?  That night I installed all the drivers --- Intel VGA, chipset, SATA, memory, etc.) and disabled hibernate via "powercfg -h off" (so that I could free up disc space by deleting hiberfil.sys).  Nothing in my limited understanding makes me think changes to Windows could affect the performance of Ubuntu but it's the only thing I know of that changed on the computer between the time suspend worked well and yesterday when it stopped functioning.

Yesterday we turned off power when the laptop wouldn't resume from suspend.  This messed up the partition I think.  Here's what I searched for in Google: mount mounting dev failed no such file directory target filesystem requested sbin init no init found ubuntu.  That got fixed by using gparted (from a live cd) to check and fix the partition.

I need help with two things.

1) How to resume from this frozen suspend?  We started cutting from an SD card and pasting to an external HDD before it went into suspend.  I don't know if it finished before suspending and I'm afraid of just turning off the power for fear of messing up some of those files.  I don't think anything was plugged into the USB yesterday when suspend first failed to resume.

2) How to fix the laptop so that suspend works again.

Right now the computer is still frozen so I can't get any more info to you about it without rebooting.  Thanks in advance.

---

### Post by raequin on 2012-10-21
I think it was suspend freezing that messed up the partition.  Because I used "sudo shutdown -h now" so it shutdown okay.  Then on turning it on again it gave the same errors about "no init found."  So fixed that with gparted again.

The suspend problem is fixed now and what I did was reverse my command in Vista to turn off hibernate.  I re-enabled it with "powercfg -h on".  Now suspend works again in Ubuntu, just like before.

Can anyone provide an explanation for how this command in Windows affected the performance of Ubuntu?

---


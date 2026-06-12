---
title: "Disabling SMP at boot time"
date: 2007-11-17
forum: General Help
---

### Post by robmiracle on 2007-11-17
I've got a problem that I think is SMP related.    Bear with me while I provide some history.

About 2.5 years a go, I got an HP box from a retail store.   It has a Pentium D 830, which was one of the first dual core machines to ship.   I was running WinXP just fine, waisting way too much time n World of Warcraft.   Then one day, the machine just stopped in the middle of a Windows session.

I rebooted, and it got to the end of the progress bar and stopped cold.   After going back and forth with tech support (and its a month out of warrenty), I discovered I could boot the Ubuntu live CD and everything ran well.    I could not install any variant of windows nor use the recovery CD's   It always stopped at the end of the progress bar.    So I said, well, its lost as a windows machine, so using the Ubuntu love CD I got all the critical data off and backed up and installed Ubuntu.  I'm pretty sure it was Dapper at the time.   

Then after it was installed, I went to install the 686 kernel.   The machine would boot, but the keyboard wouldn't work.  I would boot back to 386 fine, back to 686, not so fine.   It was at that moment, I realized the 2nd processor was probably bad.   So I left the machine running in 386 mode and have been a happy camper ever since.

Until I wanted to upgrade to Gutsy.    From Edgy (which I was running), I did an upgrade to Feisty and when it went to reboot, I got maybe 10 pixels into the progess bar and the machine just kind of stops.   I can CTRL-ALT-F1 and I see a couple of messages about ATA-1 timing out and disabiling ATA-2 (I can get the specific messages when I reboot).   But it just sits there forever. 

It seems to me I remember something about there only being one kernel now.   I can currently boot from my hard drive if I go back to the 2.6.15-27 kernel.   Or I can boot the Dapper live CD.  I recently downloaded the ISO for the Edgy install, and its showing this lockup/stall issue at boot time.   Fiesty and Gusty both hit the same problem.

So my question is the kernel trying to use the 2nd processor at this point and has the Edgy live CD thats currently downloading using this SMP enabled kernel?

And is there a way from the the live CD to boot without SMP.

At this point, I have my hard drive backed up and I'm ready to blow it away and reinstall (I didn't like how I had it partitioned anyway), but I would like the latest Ubuntu and really don't want to go back to Dapper.   

Help!

Thanks
Rob

---

### Post by bingoUV on 2007-11-17
there is a kernel parameter for exactly this : nosmp. 

open your menu.lst file, and in the kernel line, add "nosmp"  to the end. Boot.

---

### Post by robmiracle on 2007-11-17
But how can I do this on a Live CD so I can install from it?

---

### Post by atlfalcons866 on 2007-11-17
i dont think you can disable it on the livecd. The only way i think to do is disable  smp in the bios.

---


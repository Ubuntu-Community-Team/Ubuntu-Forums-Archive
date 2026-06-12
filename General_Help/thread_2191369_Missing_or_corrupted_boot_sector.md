---
title: "Missing or corrupted boot sector"
date: 2013-12-02
forum: General Help
---

### Post by Trevor4706 on 2013-12-02
I am running 12.04 in a dual boot configuration with W7.  Installation has been stable since May 2012; however, three times over the past four weeks and twice in the last two days I have received the message "Unable to find any bootable devices" when booting up the computer.  Each time the BIOS diagnostics have pointed to a missing or corrupted boot sector, and I have been able to successfully recover by using Boot-Repair.  I have also run disk diagnostics in both Ubuntu and W7 and found no sign of HDD errors or problems.  I cannot link the events to any particular action I have taken; eg, kernel upgrade, new software. etc.

Has anyone encountered a similar problem and, if so, can you suggest a solution?

---

### Post by oldfred on 2013-12-02
Post a link to BootInfo report from Boot-Repair. 
But it may not show anything either.

Did you check thru Disks or Disk Utility your hard drive Smart Status?

---

### Post by Trevor4706 on 2013-12-03
My 12.04 and W7 installations share a single HDD with multiple partitions.  I have ran multiple isk diagnostic programs on the whole disk in both OS and all report the HDD to be "healthy" with no bad sectors.  As for the Bootinfo report, I wrote down the link but have not been able to find it:(  

I am beginning to think that it's not a HDD problem but, rather, some program is over writing the boot sector.  The only thing different that happened prior to the last two instances was that the computer went into "Suspend" mode, something that rarely happens.  Is it possible something could be written to the boot sector when it suspends?

---

### Post by oldfred on 2013-12-03
I have had no issues with suspend as system is still running, but have seen threads with issues on hibernation. Do not know anything about it.
You can just rerun Boot-Repair, but if a suspend or hibernation issue it may not show anything.
When dual booting best not to use hibernation anyway.

---

### Post by Trevor4706 on 2013-12-04
My mistake.  I used the term "Suspend" when I should have used "Hibernate"; the last two events occurred after I pressed the "Hibernate" key on my keyboard, not after the computer went into"Suspend" mode, which it does automatically all the time.

Note to self: Don't use the "Hibernate" key again!

---


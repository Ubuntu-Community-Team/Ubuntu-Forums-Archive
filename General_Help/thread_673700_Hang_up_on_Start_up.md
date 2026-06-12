---
title: "Hang up on Start up"
date: 2008-01-20
forum: General Help
---

### Post by ReccaSquirrel on 2008-01-20
First, I'm typing this on my Wii.  For this reason, I'm keeping the details to a minimum.

I rebooted my Pc today not long after a software update.  Now it will not boot.  It also will not boot from Cd.

If I shut off the quiet option, I see the last log line is:

Acpi: Pci Internet 0000:02:09 [a] -> link [lnkb] -> Gsi 5(level, low) -> Irq 5

Any help would be appreciated, especially if it gets me at limited, computer access so that I can type and post boot logs.

I'm also a bit of a linux newbie so that you know.

Thanks!

---

### Post by ugm6hr on 2008-01-21
> **ReccaSquirrel said:**
> I rebooted my Pc today not long after a software update.  Now it will not boot.  It also will not boot from Cd.


I cannot see how an update would make your computer unable to boot from a CD (assuming the CD is bootable, and worked before).

Unless you have hardware problems, you should at least be able to boot (and get online) from a LiveCD.  This would also allow you to recover your data on HD, even if the worst case scenario occured and you had to reinstall.

---

### Post by banewman on 2008-01-21
Can you boot into the recovery kernel?
Are you connecting directly to the internet or through a router?

---

### Post by ReccaSquirrel on 2008-01-21
Booting into the recovery kernal doesn't work either.  The last log item is slightly different in this case.  It indicates Irq 16.

I'm connected to the internet by an ethernet connection to a 2wire dsl modem.

---

### Post by ReccaSquirrel on 2008-01-21
If it helps, I have tried the following boot options:
noapic*
pci=routeirq
pci=noapic
acpi=off**
irqpull

* This is my normal boot.
** This had a hang-up at the boot log:
Serial: 8250/16550 driver $Revision : 690$ 4 ports, Irq sharing enabled

I'm using: 2.6.20.16

---

### Post by ReccaSquirrel on 2008-01-21
Meanwhile, any ideas that might get me to recovery boot?

---

### Post by killermist on 2008-01-21
Are you able to access the bios and verify that CD is in the boot sequence before HDD?  I would think that would be the first priority to rule out a hardware failure of some type.

Once you know that booting CDs works right, ruling out hardware failure, then you could turn your attention to seeing what went wrong on the HDD.  But, until you rule out hardware failure, that's what I'd expect as a problem.

---

### Post by ReccaSquirrel on 2008-01-21
> **killermist said:**
> Are you able to access the bios and verify that CD is in the boot sequence before HDD?  I would think that would be the first priority to rule out a hardware failure of some type.

Once you know that booting CDs works right, ruling out hardware failure, then you could turn your attention to seeing what went wrong on the HDD.  But, until you rule out hardware failure, that's what I'd expect as a problem.

At first, i didn't get the question... but yes, the CD is definitely first in boot sequence.  Well, actually second.

1 Floppy
2 CD
3 HDD

I'm using the Start or Install Ubuntu option which also hangs.  This makes me suspect HW failure but I'm neither sure or able to determine which HW failed.  Though screen logs make me suspect sound card.

But you guys are the experts.

---

### Post by ReccaSquirrel on 2008-01-21
I'm giving this a bump.

I need to figure out somehow whats going on here and how to fix.  I'm just a tad frustrated.

Does it seem like a HW failure?  If so, how do I determine which piece so that I can repair/replace?

---

### Post by ReccaSquirrel on 2008-01-21
I, very happily, am typing this message instead of using the Wii's point and click system for a keyboard.

I reseated the Soundcard and was able to boot by CD.  This is the best news I've had today.

---

### Post by ugm6hr on 2008-01-21
> **ReccaSquirrel said:**
> I, very happily, am typing this message instead of using the Wii's point and click system for a keyboard.

I reseated the Soundcard and was able to boot by CD.  This is the best news I've had today.

Good news indeed. :)

---


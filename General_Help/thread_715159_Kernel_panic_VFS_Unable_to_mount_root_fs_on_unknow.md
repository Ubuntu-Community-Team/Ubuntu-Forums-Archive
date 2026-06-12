---
title: "Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2008-03-04
forum: General Help
---

### Post by feest on 2008-03-04
I recently was playing fretsonfire
:guitar:
while updating.

Somehow my already stressed out system enjoyed making screenshots and made lots of them. This locked up my computer. Because my system was updating at that moment my filesystem is now corrupt. I get this message:

Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)

Is there a way to fix this witihout losing data?

---

### Post by feest on 2008-03-05
anyone?

---

### Post by commonplace on 2008-04-18
Bump; I'm having the same problem on a lab machine here at work.

Exact same error message as the OP's.

I tried going into the recovery console, and got this:

> VFS: Cannot open root device "UUID=(the drive's UID was listed here)" or unknown-block(0,0)

Please append a correct "root=" boot option; here are the available partitions:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


It locks up there, too (just like a regular boot), and the Caps Lock and Scroll Lock keys on the keyboard (standard US 101-key) flash.

Anyone?

/Kevin

---

### Post by geraldm on 2008-04-18
try using the suggestion to append to the boot kernel line for the correct drive, partition number such as  root=/dev/hda1 

Gerald

---


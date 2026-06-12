---
title: "fsck: dirty bit is set"
date: 2020-09-01
forum: General Help
---

### Post by evanadler on 2020-09-01
This issue began when I force shutdown my system during an update. After that, I could only boot by changing the boot parameter in grub from "ro" to "rw".
Then, when I run fsck, I get the attached output every time I boot. I've pasted it here also:

`0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.`

What can I do to repair my filesystem?



As a sidenote, another thing that happens is that after adding a swap file, htop shows `OK/16.0G` swap usage, which **may** be another manifestation of this filesystem problem.

---

### Post by yapidumoac on 2020-09-01
boot from a CD and run fsck -a /dev/sda1[LEFT][COLOR=#242729][FONT=Arial] 
[/FONT][/COLOR][/LEFT]

---

### Post by evanadler on 2020-09-01
Can I do this by booting in the advanced options -> linux (recovery mode) option in GRUB and dropping to shell? Also, I assume I can replace /dev/sda1 with the volume my main filesystem is mounted on?

---


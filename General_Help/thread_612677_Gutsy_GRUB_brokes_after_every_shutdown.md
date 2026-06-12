---
title: "Gutsy GRUB brokes after every shutdown"
date: 2007-11-14
forum: General Help
---

### Post by anv on 2007-11-14
I installed Gutsy yesterday, and every time I have shut down, it has broken the Grub, giving every time same: error 18, I have installed Grub again from the rescue mode and then it starts without cd, but like this morning again when I booted machine, it told that Grub ERROR 18.

---

### Post by anv on 2007-11-15
So Grub breaks after every shut down Giving error 18, I have to use rescue mode to install Grub again. 64-bit xubuntu Gutsy Gibbon is in use...anyone?

---

### Post by jespdj on 2007-11-15
I had a similar problem on my desktop PC. I searched around on Internet and found out that some SATA harddisks and CD drives have this problem. Try searching for "grub error 18" on Google.

On my computer, the problem was fixed by changing the boot order in the BIOS: put the harddisk first, not the CD drive, in the boot order.

---

### Post by anv on 2007-11-15
I haven't ever before met this error, only just after this new release, and all my harddrives and DVD-Rom are ide, I tried to change the order in bios didn't help. I just wondered why it boots after I repair the Grub and what breaks the GRUB after it shutdowns or while working in desktop.

---


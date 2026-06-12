---
title: "What do you mean Wubi doesn't suspend? =)"
date: 2008-03-06
forum: General Help
---

### Post by stoffe on 2008-03-06
Hello, just read this: [https://wiki.ubuntu.com/HardyHeron/Alpha6](https://wiki.ubuntu.com/HardyHeron/Alpha6)

It says that suspend and hibernate doesn't work in Wubi installations - lucky me that didn't read that, because I've been using suspend succesfully since I installed the alpha 5 version. ;)

Ok, so what I really wonder is: is that just advice because it is borked on a majority of machines, or shoudn't it work at all, or could there be potential data loss or something? Should I avoid it?

---

### Post by ago on 2008-03-06
Did you install on fat or on ntfs?

---

### Post by stoffe on 2008-03-06
NTFS, it's a HP 2710p laptop that came with Vista Business preinstalled (work, you  know).

---

### Post by ago on 2008-03-06
Ah that's great news then! In fact I hadn't tested suspend with the new kernel, might well be that the issue was fixed... I had been asking the kernel team to look at it for a while, but did not have much feedback so far.

---

### Post by ago on 2008-03-06
I cannot test until later on tonight, can someone else please confirm this?

---

### Post by elfejoyeux on 2008-03-06
Hi !
I've just tested suspend on wubi 8.04 rev 444 (ubuntu up to date) : it works well :-)

The host is XP pro with NTFS.
The computer is a dell optiplex GX520 (p4HT, HD SATA)...

---

### Post by ago on 2008-03-06
Music to my ears... :D

---

### Post by ago on 2008-03-07
I can confirm that suspend works!!!

Thanks a lot stoffe!

---


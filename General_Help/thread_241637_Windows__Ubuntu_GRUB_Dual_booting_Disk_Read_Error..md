---
title: "Windows / Ubuntu GRUB Dual booting Disk Read Error."
date: 2006-08-22
forum: General Help
---

### Post by Pandroid on 2006-08-22
Hey folks.

I'm attempting to dual boot Ubuntu and Windows XP on the same system, though I've run into a few problems.

I can boot into ubuntu fine, but when I choose to boot into XP from GRUB, it throws a diskread error.

My drive is partitioned as so:
/dev/hda1    =    Ubuntu Install
/dev/hda2    =    Swap
/dev/hda3    =    Windows partition

When I first tried, I installed windows first, then linux and had the problem. I then installed windows again, reinstalled grub and had the same problem.Finally, I ran fixboot on recovery console in xp and it still has the same problem.

Here's the grub entry for windows.

```
title		Windows XP Professional
root		(hd0,2)
makeactive
chainloader	+1
```

Any help will be greatly appreciated.

Thanks.

---

### Post by Pandroid on 2006-08-23
Bump.

Any help will be greatly appreciated.

---


---
title: "Major big bug"
date: 2013-05-14
forum: General Help
---

### Post by vincentlegawa on 2013-05-14
Hi Im using ubuntu 12.2 and for a while I had this message opening my computer \tmp is missing or not ready but it would open. Now I had a message that I should run synoptic or perform a phrase apt..... ( forgot the rest) but non worked and now I had another message saying that I need to reinstall linux-image-3.5.0-28-generic (full message was :c'type'exception.System errors'>'E:the package linux-image-3.5.0-28-generic needs to be reinstalled but I can't find an archive for it

I tried to repair package in recovery mode but the linux image 3.5.0.28-genieric does not appear I tried with the 3.5.0-28 generic but nothing to do now my computer wont event start    please help me

---

### Post by ajgreeny on 2013-05-14
Hold **shift** when you power up the machine and the grub menu should appear.  From that choose the previous kernel that you have on the machine to see if that will boot OK.  If it does you can then reinstall the kernel 3.5.0-28 to see if that solves your problem.

PS:  On some machines using UEFI instead of legacy BIOS, you need to continually press and release Esc to get the grub menu; from there it should be the same procedure.

---


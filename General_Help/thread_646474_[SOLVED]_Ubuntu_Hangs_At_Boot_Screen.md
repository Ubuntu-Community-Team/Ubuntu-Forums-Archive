---
title: "[SOLVED] Ubuntu Hangs At Boot Screen"
date: 2007-12-21
forum: General Help
---

### Post by MidianLies on 2007-12-21
Hello,

So after finally managing to successfully install Ubuntu to a freshly created partition on my HP dv9000 notebook (Originally running Win XP Media Center Edition Version 2000 SP2), every time I attempt to boot to Ubuntu, the computer hangs indefinitely at the boot screen, and the orange progress bar only makes it up to the first three segments.

I have left it at this point for over an hour in hopes that it would eventually boot, but no luck.

I would really appreciate any advice on what is causing the hang and how I can remedy the problem.

Thanks.

---

### Post by Pumalite on 2007-12-21
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by MidianLies on 2007-12-21
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

LOL. Thanks for your response man. I read the first thread before posting, but not the second. And I'm glad you posted it. Its basically telling me that I have no hope of running this OS on my laptop and to use Feisty. Hopefully things will be easier.

---

### Post by MidianLies on 2007-12-21
Yea, I downgraded from Gutsy to Feisty. Still doesn't work. I'm just loving Linux.

---

### Post by Pumalite on 2007-12-21
Do a clean install of Feisty.

---

### Post by MidianLies on 2007-12-21
Uh, whats a clean install.

---

### Post by MidianLies on 2007-12-22
Bump Bump.

---

### Post by Pumalite on 2007-12-22
Get gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it. Make a partition for Feisty and install to it from the Alternate CD.

---

### Post by MidianLies on 2007-12-22
Yea, I already had a partition and have been using the Alternate CD. The Live CD never worked for me. But a user in the official HP dv9000 thread suggested that I install from the alternate CD with 'noapic' added as a boot option. That eliminated the boot hang, and at this very moment I am booted to my Ubuntu desktop and its working well.

---


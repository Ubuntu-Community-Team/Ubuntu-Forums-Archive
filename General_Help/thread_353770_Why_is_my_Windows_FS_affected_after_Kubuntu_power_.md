---
title: "Why is my Windows FS affected after Kubuntu power failure?"
date: 2007-02-05
forum: General Help
---

### Post by mibadt on 2007-02-05
Hi,
I've a dual boot (Kubuntu Edgy/XP). Recently, I was "lucky" and has 2 power failures while in Kubuntu. While Kubuntu (ext3) recovered flawlessly, in both times when I tried to open XP (NTFS) after the crash, XP initially found FS errors (which, luckily, it was able to fix). In all former XP sessions, I both booted into XP without problem and "clean" shut down Xp afterwards, Thus, I suspect XP FS was damaged due to the fact that Kubuntu mounted it.
Any idea what's going on and how can I "harden" my XP against similar accidents in the future?

TIA
Michael Badt

---

### Post by lamego on 2007-02-05
Was it mounted readonly with the standard driver or rw using the ntfs3g ?
If it was mounted ro it shouldn't be affected...

---

### Post by glotz on 2007-02-05
If you enjoy power breaks regularly, I strongly suggest you invest in a UPS device. If the software manages to survive the breaks, your hardware doesn't like them at all. [http://en.wikipedia.org/wiki/Uninterruptible_power_supply](http://en.wikipedia.org/wiki/Uninterruptible_power_supply)

---

### Post by mibadt on 2007-02-05
Thanks,

1. The NTFS is mounted ro using the standard!
2. I'm going to buy a UPS.

Regards,
Michael Badt

---


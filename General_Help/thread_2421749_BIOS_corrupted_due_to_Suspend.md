---
title: "BIOS corrupted due to Suspend?"
date: 2019-06-26
forum: General Help
---

### Post by blunt0 on 2019-06-26
Hi, I have been using Ubuntu 18.04.2 LTS for the last few months, and had a few issues but thanks to help from the community I managed to solve them, however this one worries me greatly.

So sometimes when Ubuntu goes into "Suspend" mode, my PC is not able to enter desktop mode, and effectively freezes, which is annoying, but not that big of a deal.
But yesterday, It corrupted my BIOS, luckily my motherboard has a dual BIOS and I managed to recover, I re-flashed my main BIOS and everything works fine.

But I feel very uneasy continuing like this, as I do not want to brick my hardware.
I have never had any BIOS issues before, although my MBoard is old, it is still serving me well. Gigabyte x58-UD7

How should I proceed?

---

### Post by Autodave on 2019-06-26
First of all, I would check the MB battery.  You said that it was old, so chances are the battery is very weak/dead.

---

### Post by blunt0 on 2019-06-26
I doubt that is the problem as I have replaced it about a year ago, would it drain so fast?
But it is easy enough to check, although I don't have time today, I will certainly check it.

---

### Post by blunt0 on 2019-06-26
I have measured the voltage of the MB-battery with a multimeter set to the battery check setting, and it measures 2.96v out of 3v, surely that should be sufficient?

---

### Post by MartyBuntu on 2019-06-26
Have you tried a different kernel?

---

### Post by Autodave on 2019-06-26
> **blunt0 said:**
> I have measured the voltage of the MB-battery with a multimeter set to the battery check setting, and it measures 2.96v out of 3v, surely that should be sufficient?

That should be fine.

---

### Post by blunt0 on 2019-06-27
> **MartyBuntu said:**
> Have you tried a different kernel?

I am trying Pop_OS right now, so far I do not have any sleep issues yet, I do not know if it is a different kernel though it is also the 18.04 LTS version, I do not have much flexibility as I need OpenCL compatibility from AMD.

To be honest I am not really trying to replicate the issue, as corrupting the BIOS seems like a very bad thing, I'm just trying to prevent this from happening again.

---


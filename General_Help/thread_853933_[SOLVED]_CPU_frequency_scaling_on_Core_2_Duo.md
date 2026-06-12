---
title: "[SOLVED] CPU frequency scaling on Core 2 Duo?"
date: 2008-07-09
forum: General Help
---

### Post by Epistaxis on 2008-07-09
Has anyone successfully enabled the Intel SpeedStep system on a Core 2 Duo in 8.04? If so, how?

I've tried a few different things with no success - it seems as though my system is incompatible with the available Linux packages, even though Windows recognizes it just fine. If it's worked for someone else, I'll keep trying. Or if someone can verify that it doesn't work, I'll stop wasting my time. Or, if you just have a suggestion that you haven't actually tried yourself, I'll show you where it goes wrong. :-)

---

### Post by sdennie on 2008-07-09
As long as your BIOS supports it properly it should work.  What type of machine do you have?  What is the output of:

```

cpufreq-info

```

(It may give you instructions on how to install that first.)

---

### Post by Epistaxis on 2008-07-09
> **vor said:**
> As long as your BIOS supports it properly it should work.  What type of machine do you have?  What is the output of:

```

cpufreq-info

```

(It may give you instructions on how to install that first.)

My machine is an Intel Core 2 Duo E8500 on an Asus P5K Deluxe. As I said, frequency scaling works in Windows XP, so BIOS supports it and it's enabled. The output from cpufreq-info is:
```

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```

---

### Post by sdennie on 2008-07-09
I've seen several threads about this kind of thing in the Hardware & Laptops sub-forum.  You may want to search there.  It could be that your BIOS isn't giving the information linux needs to make the scaling work or it's doing it in a non-standard way.  If you don't find anything in Hardware & Laptops, you may look for a BIOS update for your machine.

---

### Post by Epistaxis on 2008-08-02
I think I solved my own problem. In the Asus P5K Deluxe's BIOS, I'd manually set my CPU clock ratio to 9.5. I set it back to Auto by manually typing in "Auto" (there was no list of options) and now the frequency scaling works correctly in Ubuntu as well as in Windows XP.

---


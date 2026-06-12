---
title: "Increased power consumption with 5.0.0-35 kernel or later"
date: 2019-12-18
forum: General Help
---

### Post by Ascaris_ on 2019-12-18
On Kubuntu 18.04 (fully updated), I've enabled the HWE kernel stack. I've noticed that both of my laptops using this kernel have shown increased power consumption lately, with the battery lasting noticeably shorter than it used to, and with Powertop reporting a higher rate of idle discharge than in the past.  I've tracked it back to when I upgraded the kernel from 5.0.0-32 to 5.0.0-35, and it's confirmed by Powertop's Package C-states reports under Idle Stats.  Both laptops have TLP installed, fwiw.  Powertop has revealed some interesting information related to this.

With 5.0.0-32, both of my laptops (one Coffee Lake i7, one Apollo Lake "Pentium" N-series) report significant percentage spent in C-states in the "Package" column when the CPU is idle on battery, in addition to those in the "Core" column.  

When I boot with 5.0.0-35, -36, or -37, on battery, in Powertop, the C-states reported in the Package column are stuck at 0% in both laptops, apart from short blips of C2 that quickly disappear.  These versions all have increased power consumption as a result.

Given how popular laptops are, I would find it hard to believe that I am the first one who has noticed this, but any attempts to find reports of this issue have turned up nothing.  Is anyone else seeing this, and does anyone have a workaround?

---

### Post by Ascaris_ on 2019-12-27
Got this figured out, I think.  Somewhat.

One of the changes in mainline kernel 5.3.11 caused this.  The problem was not present in 5.3.10, but is present in all newer releases of 5.3.  Ubuntu must have backported the change that caused the problem to the 5.0 kernel for the 5.0.0-35 release.  

The problem remains in mainline 5.4 releases, but is fixed in 5.5.0 RC3. 

Hopefully Ubuntu will backport the fix, whatever it was, so that we won't need to wait for 5.5 to come down the line, which will probably be quite a while.

---


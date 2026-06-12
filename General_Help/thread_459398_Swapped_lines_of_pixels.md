---
title: "Swapped lines of pixels"
date: 2007-05-30
forum: General Help
---

### Post by -Phi- on 2007-05-30
I have a Toshiba Lifebook s7110 that for the most part runs Xubuntu Feisty just dandy. However, every once and a while when I boot and always when I resume from standby, lines of pixels on my screen swap. I've attached a screenshot where you can see the line of pixels on the right side of the screen, and the location they're taken from on the left. Sometimes the lefthand side has a misplaced row of pixels too.

I'd suspect a hardware issue, but the cursor can run over the line without looking weird. Rebooting usually solves the issue temporarily.

The graphics card is an intel 950 and I have 915resolution installed.

Any suggestions?

- Phi

---

### Post by wpshooter on 2007-05-30
What is the reason for running Xubuntu instead of Ubuntu or Kubuntu, are you lacking in memory ?

---

### Post by -Phi- on 2007-05-30
Personal preference. It amuses me to run Beryl with Xfce.

But the line happens independent of whether the window manager is Beryl or xfwm4 so I'm not clear that the issue lies with either one.

- Phi

---

### Post by -Phi- on 2007-05-30
For the heck of it I installed ubuntu-desktop, and a GNOME session has the exact same messed up line of pixels. So I guess the fact that I'm using Xubuntu is irrelevant in this case.

- Phi, now tracking down the last 200MB of stuff that ubuntu-desktop left behind

---

### Post by -Phi- on 2007-06-11
Pixel swapping problem solved by replacing the i810 driver with the intel driver.

New problem: hibernate, suspend, and occasionally even shutdown hang with a blinking screen of blocky static.

- Phi

---


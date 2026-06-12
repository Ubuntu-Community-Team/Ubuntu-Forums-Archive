---
title: "All things modules cause soft lockup on boot"
date: 2008-07-07
forum: General Help
---

### Post by klange on 2008-07-07
This machine is going to be the death of me. About a year ago I tried to get Feisty on the dang thing, but the kernel didn't even load. Things have gotten better, but I'm still in a major pickle.

Anyway, I've got an old Dell mobo (I have to check the model #, for now, details below) as part of a fairly nice "spare parts" machine. Now, Windows runs fine (like I said, had trouble with Ubuntu a while ago, and just needed the thing to run *something*), though it has some kinks (insert a serial cable and Windows... "does its thing" so to speak [BSOD]). When I pop in my Hardy disk, which I've already checked to be perfectly clean and clear of any defects, the kernel loads fine and I get, after the long loading sequence, to the actual boot. It gets through basic networking and such, but crashes while loading modules. First modprobe dies and udevd spews a long error report claiming:
```
BUG: soft lockup - CPU#0 stuck for 11s! [udevd:####]

Pid: ####, comm: udevd Tainted: G      D (2.6.24-16-generic #1)
```
And so on.
Clearly some major problems, as this continues every "11s" with the same message (same address codes, too).

Details on the mobo while I search for the original machine's product number:
- From a not-too-old Dell desktop
- 4 PCI slots
- AGP
- DDR RAM
- Pentium 4 (1.8GHz, though I'm pretty sure that's not what it came witH)
- Pheonix BIOS that considers a lack of a front board to be a fatal error (which is a pain the ***)

Google has not helped me in my quest for answers, giving me only unresolved threads in foreign languages, surely we here at UF can do better?

---


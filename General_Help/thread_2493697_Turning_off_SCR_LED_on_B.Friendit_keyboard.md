---
title: "Turning off SCR LED on B.Friendit keyboard"
date: 2023-12-22
forum: General Help
---

### Post by MZ250Supa5 on 2023-12-22
I have a B.Friendit KB700-Pro keyboard, (nice illuminates aluminium keyboard that's robust and keys don't wear out in 5 minutes) but I have recently hit a problem: the SCR LED light is permanently illuminated. I have encountered the issue before, and I found a solution, but I'm damned if I can find it again. All I can find are long-winded and variously complicated ways of turning off Scroll Lock that just don't work - and far more suggestions for turning Scroll Lock on! 

It's very frustrating because with Scroll Lock activated I cannot, for example. use the PS key to print screen, or use the Ctrl-Alt-T to summon a Terminal, (not that that's 100% guaranteed to work on Ubuntu Mate these days anyway) or uses complicated keyboard/mouse combinations for certain types of navigation in OpenSimulator.

As is usual with most things computer, the prospect of people actually choosing to use a Linux distro and not Windows or Mac seems to have completely escaped the manufacturers of this keyboard, so no instruction on how to enable/disable Scroll Lock on Linux are offered, and neither the Windows or Mac options works, of course.

---

### Post by MAFoElffen on 2023-12-22
If using Xorg, the you could try
```

xset -led named "Scroll Lock"

```
That utility doesn't work with Wayland...

---


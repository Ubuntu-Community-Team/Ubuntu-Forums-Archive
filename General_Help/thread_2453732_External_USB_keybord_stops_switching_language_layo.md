---
title: "External USB keybord stops switching language layout fater suspend"
date: 2020-11-16
forum: General Help
---

### Post by simone-c on 2020-11-16
Hi,

I have two different brand new Ubuntu 20 installations that are both affected by the same strange behavior.

After a suspend to RAM an extrenal USB keyboard is no longer able to switch keyboard layouts using traditional ALT+SHIFT or CTRL+SHIFT combinations. Windows+Space keeps working. The built-in laptop's keyboard is not affected, after the suspend both alt+shift and ctl+shift still works. It's only USB keyboard affected. Tested different external keyboards. There was no such issue in Ubuntu 18 bionic.

Steps to reproduce.
1. Set up language layout to switch using either ALT+SHITF or CTRL+SHIFT
2. Verify that both laptop's built-in keyboard and an external USB keyboard work
3. Suspend to RAM
4. Wake up
5. Built-in keyboard still works
6. The external USB keyboard ignores keyboard layout switch

Please suggest what could be investigated to collect more info for possible bug report

Thanks

---


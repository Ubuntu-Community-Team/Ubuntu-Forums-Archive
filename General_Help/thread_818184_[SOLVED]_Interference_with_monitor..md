---
title: "[SOLVED] Interference with monitor."
date: 2008-06-04
forum: General Help
---

### Post by bdandemw on 2008-06-04
Have just installed ubuntu works fine except that vertical lines are generated on the dislplay. A permanent line on the left and transient lines on the right when the mouse moves. Have tried cahanging the display resolution but this has no effect. Current resolution is 1280x1024. Any ideas, thanks in advance.
Brian

---

### Post by overdrank on 2008-06-04
> **bdandemw said:**
> Have just installed ubuntu works fine except that vertical lines are generated on the dislplay. A permanent line on the left and transient lines on the right when the mouse moves. Have tried cahanging the display resolution but this has no effect. Current resolution is 1280x1024. Any ideas, thanks in advance.
Brian

Hi and welcome, could you tell us some system specs and the graphics card used? You can use the command ```
lspci
``` In the terminal located under applications, accessories.

---

### Post by bdandemw on 2008-06-04
Thanks  for reply.
 system  is Winfast main board with integrated VGA lspci gives the following info:

00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

Incidentally monitor is ok on Win.....

---

### Post by overdrank on 2008-06-04
> **bdandemw said:**
> Thanks  for reply.
 system  is Winfast main board with integrated VGA lspci gives the following info:

00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

Incidentally monitor is ok on Win.....

Hi and the SIS chipset is not supported well in linux but you may search the forum for the graphics and find some ideas. In the past some users have changed the default depth from 24 to 16.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
Good luck!

---


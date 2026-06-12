---
title: "Fresh 14.04 LTS failed to boot"
date: 2015-01-08
forum: General Help
---

### Post by kruget on 2015-01-08
Login screen OK, but after entering user and password it stuck at default screen with "ubuntu 14.04 LTS" at bottom left of the screen with mouse cursor still working. 

Longer waiting resulted in total hang, screen turned into diagonal strips as if something wrong with VGA card.

The mainboard is old BIOSTAR MCP6P M2+, Windows 7 said it has internal Nvidia geforce 6150SE nforce 430. 

Windows 7 runs fine in this, old ubuntus also runs fine. How to make  14.04 run in this?

---

### Post by mörgæs on 2015-01-09
How does it work in a live boot of X/Lubuntu?

---

### Post by kruget on 2015-01-11
Live CD (USB installer) works partially. When I choose "try ubuntu", it ended with same error, but if I choose "install ubuntu" it run ok and the installation completed.

---

### Post by kruget on 2015-01-14
Solved by installing Lubuntu. Tho same problem happened when wake up from locked screen saver, it cured after installing the proprietary driver in "additional driver", pick the one with "updates" behind it.

---


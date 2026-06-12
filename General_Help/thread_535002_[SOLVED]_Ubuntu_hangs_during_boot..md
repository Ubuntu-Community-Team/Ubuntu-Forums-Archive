---
title: "[SOLVED] Ubuntu hangs during boot."
date: 2007-08-25
forum: General Help
---

### Post by sci-fi guy on 2007-08-25
Hi, I have a rather irritating problem: When Ubuntu boots, it will hang for about a minute when the bar on the loading screen is about 3 "cells" from the center.

---

### Post by merlinus on 2007-08-25
Ubuntu is probably loading some modules.  You can watch what is happening by removing "quiet" from the kernel boot line by editing /boot/grub/menu.lst.

Or you can press e at the grub menu, arrow down to the kernel line, and edit it there for only that one time.

-merlin

---

### Post by sci-fi guy on 2007-08-26
Sweet... It hangs at "configuring network interfaces" or something similar.

---


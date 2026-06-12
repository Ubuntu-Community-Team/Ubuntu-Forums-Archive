---
title: "Can't log in to ubuntu"
date: 2017-11-04
forum: General Help
---

### Post by jphyde on 2017-11-04
A couple of days ago my Ubuntu 17.04 crashed.  When I tried to log back in I got the grub prompt, and entered "exit", then a new, smaller font grub prompt displayed and I entered "exit" again, but the os selection screen did not appear and it logged me directly into my dual boot Windows 10 (ugh!).  How do I get ZestyZapus back???

---

### Post by Impavidus on 2017-11-05
Maybe grub couldn't find its configuration file and therefore couldn't show the menu, presenting you with the prompt instead.

Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) from a live disk. Don't run the recommended repair, but create a BootInfo summary and post the link here. That should tell us what's going on.

---


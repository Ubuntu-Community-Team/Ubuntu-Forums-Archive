---
title: "startx freezes system"
date: 2014-03-29
forum: General Help
---

### Post by mam214 on 2014-03-29
Just rebooted, and suddenly running startx freezes the system.  Screen is replaced by a solid cursor in the upper left corner, so I don't know where it's hanging or what errors I get or anything.  Can't switch ttys, I have to do a hard reboot.  Ubuntu 13.10, kernel version 3.11.0, graphics card Radeon 5450, fglrx_pci driver.

At a total loss, any help would be greatly appreciated!

e: I've ssh'd into the system while it's frozen and it doesn't look like X is running.  Anything I should look around for that would be helpful?

Solved - Reran fglrx from apt with 'apt-get install fgrlx'. I think opencv installed something from nvidia which may have messed stuff up.

---


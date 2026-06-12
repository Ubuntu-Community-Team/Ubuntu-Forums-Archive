---
title: "[SOLVED] Editing boot menu problems"
date: 2008-06-04
forum: General Help
---

### Post by Robotech47 on 2008-06-04
Well I am having a slight problem, nothing system critical but just really annoying. I am currently running Ubuntu 8.04 on a dual booting laptop with windows xp pro. The problem that I am having is that every time Ubuntu does a major update, it adds another version (sort of) to the boot menu list. It looks like this,

Ubuntu 8.04, kernel 2.6.24-18-generic
Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-14-generic
Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
Ubuntu 8.04, memtest86*
Other operating systems:
Microsoft Windows XP Professional

I really just want my most current version of Ubuntu to show up boot list menu along with memtest and win XP. Any help on how to do this would be greatly appreciated.

---

### Post by logos34 on 2008-06-04
change 'howmany' option in /boot/grub/menu.lst:

[http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall](http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall)

or 

comment out (hash '#') entries so they don't show:

[http://users.bigpond.net.au/hermanzone/p15.htm#hide_items](http://users.bigpond.net.au/hermanzone/p15.htm#hide_items)

---


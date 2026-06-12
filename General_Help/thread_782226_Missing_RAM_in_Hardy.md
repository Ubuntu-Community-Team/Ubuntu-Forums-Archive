---
title: "Missing RAM in Hardy"
date: 2008-05-04
forum: General Help
---

### Post by strick242 on 2008-05-04
I just installed a 2G ram chip in my compaq v5207nr laptop running hardy.  It originally had a 512 chip.  The BIOS correctly shows 2.5 gigs of ram but system monitor in gnome only reports 2 gigs.  Where did the other 512 go?  How do I enable it?  Below is the results of uname -a
Linux ubuntu-compaq 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
Thanks in advance!

---

### Post by chewearn on 2008-05-05
Do you have integrated graphics, which use shared RAM?  Then, it's likely the 512MB is used by the graphics chip.

---


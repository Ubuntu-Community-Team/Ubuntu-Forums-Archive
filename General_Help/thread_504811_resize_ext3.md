---
title: "resize ext3"
date: 2007-07-19
forum: General Help
---

### Post by atlfalcons866 on 2007-07-19
hi 
i might be forced to install winblows. I found my old games that i used to play back in my windows xp days. Is there a way to resize the ext3 parttion. 
here is my fdisk


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1580    12691318+  83  Linux
/dev/sda2            1581       19335   142617037+  83  Linux
/dev/sda3           19336       19457      979965   82  Linux swap / Solaris

Or better yet can i use virtual box to play games on my xp virtual machine?

---

### Post by brent113 on 2007-07-19
Yes you can resize it.  The easiest way is to use GParted.  Boot from the live CD and it's in the System->Administration menu.

Also, you can use a virtual box, but they work by emulating a set of hardware, often ones that may not work with directX.  Some games may work, some games may not.

Also look into Crossover, it allows you to run windows programs in linux natively (it uses code from the wine project, along with proprietary code).  Not all games are supported, but many are.

---


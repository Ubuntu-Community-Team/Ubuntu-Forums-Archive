---
title: "Factory reset with Windows 8 and Ubuntu 14.04 Dual Boot?"
date: 2014-10-11
forum: General Help
---

### Post by macin2 on 2014-10-11
I need to completely factory reset my computer to its fresh-out-the-box state. I have Ubuntu 14.04 dual booted with Windows 8 pre-installed on an HP computer. Can I just go about resetting my computer as normal? Or do I need to take additional steps to make sure my computer is back to its original condition? I am not as technically savvy as many here so my apologies if this may seem as obtuse or an unknowledgeable question ;)

---

### Post by oldfred on 2014-10-12
It seems to depend on vendor & model. Do not know about HP.

Some expect to see the exact partitions and sizes that you had and do not reinstall a boot loader. Not so sure with newer UEFI systems. Windows is not good about seeing Linux partitions and often rewrites a partition table without them. 

Are you keeping any of Ubuntu? If so I would backup /home and list of installed applications to make it easy to reinstall. 

At the very least make a Windows repair flash drive before doing anything else.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---


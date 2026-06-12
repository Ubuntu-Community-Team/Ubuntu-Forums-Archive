---
title: "Partition"
date: 2007-06-05
forum: General Help
---

### Post by iskandarhai on 2007-06-05
Sorry, this is a Windows question. I can't find diskmgr.msc on my Vista (home premium) machine. 
Intel core 2 Duo, running 32-bit OS
I can't find fdisk either. 
I need to find out about my drives and partitions before I install Ubuntu 

Much thanks in advance, 
Iskandar

---

### Post by merlinus on 2007-06-05
gparted live cd from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by iskandarhai on 2007-06-05
Thanks. But I was looking for some programme within Windows that can tell me information about my disks and their partitions, etc. before I install Ubuntu. 
The Ubuntu CD tells me to run diskmgr.msc from within Windows but Windows tells me that it doesn't have diskmgr.msc and I could not find fdisk programme either (in Vista home premium). 

Sincere thanks, 
Iskandar

---

### Post by Rossiter on 2007-07-09
Hope this info will help you.  It's all based on XP Pro, but maybe it will apply to Vista as well.
diskmgr.msc does not exsist in XP Pro either.  It appears to be a typo in the Ubuntu documentation.  Try this in the "Run..." dialog instead.  Type [C:\WINDOWS\system32\diskmgmt.msc], without the brackets.
FYI, fdisk went away with WinMe.  In XP Pro you must install the "Microsoft Windows Recovery Console" from the original install disk.  This will set up a dual boot option between XP's GUI and XP's Command Console (Looks a lot like DOS) where fdisk type functions reside.  The XP equivalent fdisk is diskpart.

---


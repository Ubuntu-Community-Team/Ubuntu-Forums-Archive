---
title: "Change the partition?"
date: 2013-01-13
forum: General Help
---

### Post by RM33 on 2013-01-13
I have a dual boot set up. When I first start the computer I get a black and white screen. In it I see a menu with options to run Ubuntu or Windows.

I need to change the size of the partition. How do I do this?

---

### Post by offgridguy on 2013-01-13
> **RM33 said:**
> I have a dual boot set up. When I first start the computer I get a black and white screen. In it I see a menu with options to run Ubuntu or Windows.

I need to change the size of the partition. How do I do this?
To change windows partitions you need to use the windows task manager,
also called disk management if you have windows 8.


Start screen search, type in 'Disk Management" > select "Settings' > select 'Create and format hard disk partitions"

---

### Post by Herman on 2013-01-13
> I need to change the size of the partition. How do I do this? 	
Are you wanting to make Windows or Ubuntu larger or smaller? 

If you need to shrink Windows, it's okay to use the Windows Disk Management Utility providing you have Vista or later. The Disk Manager in Windows XP was buggy and can corrupt your partition table.
Another problem with Windows Disk Management even in up to date versions is you may not have the ability to shrink Windows any further, especially if the partition has already been resized to nearly half of its original size in an earlier operation. This is due to 'immovable files', which usually comprise the MFT, and the Windows page file. You can turn the page file off if you need to. That might get you a little more room. Remember to turn the page file back on again later. Windows cannot move its MFT though.
 It's usually quicker and easier to use GParted for shrinking Windows, especailly if you want to shrink Windows to a small size. No prior defragging is needed, which saves a lot of time, but GParted will induce a file system check next time you boot Windows and many Windows users seem to be scared of file system checks.  When the file system check is working just be patient and allow the file system checker to run its full course. You should never cancel a file system check in mid stream. To make Windows bigger it doesn't matter which partition editor you use.

Ubuntu partitions are easy to resize from the right, but the start point at the left-hand side, (as represented by graphical  representations in most popular partition editing programs), is quite a slow operation. Depending on how much work you have already invested into upgrading and customizing your Ubuntu installation, it might almost be quicker to re-install Ubuntu.

---


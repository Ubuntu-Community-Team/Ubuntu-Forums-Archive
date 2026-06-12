---
title: "Ubuntu no longer boots"
date: 2008-06-20
forum: General Help
---

### Post by wabirge on 2008-06-20
I am a Linux newbie but experienced in Windows.  I have XP and Vista installed on separate partitions of HD1 and several months ago installed Ubuntu 7 into a partition on HD2. (I recently upgraded to 8.04 with no problems.) I use Acronis OS Selector as a boot manager and until now have been able to boot into any of these 3 OS's at startup.

Yesterday I used Acronis Disk Director 10.0 to make minor changes in the sizes of the XP and Vista partitions on HD1 but did nothing to HD2 where Ubuntu lives.

Immediately after making the changes I found Ubuntu had disappeared from my OS Selector options.  I tried booting directly into HD2 but got a black screen.  I assume that somehow the Ubuntu boot record got destroyed or can't be found.

I can run the demo version of Ubuntu 7 from my distribution disk and with it I can access all the files on my permanent Ubuntu installation on HD 2.  Can someone tell me what to do to restore the boot record or fix whatever else is wrong?

Many thanks for your help!

---

### Post by logos34 on 2008-06-20
[Reinstall grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351") of the second hard disk where ubuntu is.  Then select the boot disk in the Bios.  Also, for good measure, repeat steps a second time but write it to the bootsector of the ubuntu root partition (i.e. 'setup (hd1,**?**)')

---

### Post by wabirge on 2008-06-20
I followed the reference you provided and found the grub files to be on (hd1,2). I ran setup successfully for that location and reinstalled Acronis OS Selector from my XP OS.  It found and booted to Linux right away so the problem is solved.

Thanks again!

---

### Post by logos34 on 2008-06-20
Sure thing.  Enjoy!  And mark the thread 'Solved' if you could.

---


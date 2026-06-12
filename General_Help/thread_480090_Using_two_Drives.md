---
title: "Using two Drives"
date: 2007-06-21
forum: General Help
---

### Post by Brian Reynolds on 2007-06-21
I am presently using one drive for both Windows and Ubuntu. When I boot up I get the choice between using Ubuntu or using Windows XP. It works okay.
What I want to do is use Windows XP on one drive and Ubuntu on another drive. Can anyone suggest a way that will allow me to get the choice between using Ubuntu or Windows XP as it presently does on the oine drive?
Brian.

---

### Post by gfixler on 2007-06-21
Until you get a real answer from someone more knowledgeable, I believe this would simply be down to your grub menu.lst file, which you can view with:

vim /boot/grub/menu.lst

I've got this at the bottom for my Windows partition, on partition 0 of hd0:

title       Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader +1


My Linux kernel listed elsewhere in there has root at (hd0,1), as it's on the second partition. You could probably change that to a different drive, say hd1, if that's where Windows was, and then just make sure your BIOS boots the Linux drive first.

That's my guess, anyway. Grub is what gives you that menu up front, and sends you off to the right place, and its menu.lst is what's read to create the startup menu. Just back it up, and have an escape plan, in case you mess it up!

---

### Post by logos34 on 2007-06-21
start reading here, contains great links:
**[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)**

---


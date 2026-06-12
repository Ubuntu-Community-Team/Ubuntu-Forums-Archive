---
title: "Grub problems w/ dual boot - please help yet another noob who's having issues"
date: 2005-05-08
forum: General Help
---

### Post by malacoda on 2005-05-08
Ok, I'm a noob having issues dual booting with GRUB.  I've tried several variations of the /boot/grub/menu.lst edits provided in other threads but still no luck...

Here's what I've got:
Gigabyte mobo (GA-K8NF-9) w/ AMD Athlon 64
Samsung SATA with WIN XP installed on it
West. Dig. IDE w/ Ubuntu installed on it

I installed GRUB as instructed during Ubuntu install.
If I then restarted, and chose WinXp on the GRUB screen I got the following error:
root(hd1,0)
filesystem type unknown partition type 0x7
save default
makeactive
chainloader +1

As per other threads on this issue I've tried (thru gedit in the root shell):

title Windows NT/2000/XP
map(hd0)(hd1)
map(hd1)(hd0)
root(hd1,0)
savedefault
makeactive
chainloader +1

I also tried the same thing with sda1 subsituted in all instances for hd1. No luck.
then I tried...

title Windows NT/2000/XP
map(hd0)(hd1)
map(hd1)(hd0)
root(hd1,0)
rootnoverify(hd1,0)
makeactive
chainloader +1

again, this was also tried with sda1 substituted for hd1 in all 4 lines but still no luck.

I've also tried all 4 combinations described above with my hdd BIOS access mode set to LBA for the IDE drive and LARGE (only option other than AUTO) for the SATA drive...

Still no luck.  
At different points, depending on what combination I was in the midst of trying, the error would change; in one case it was 'FST ext2fs partition type 0x83   error 13: invalid or unsupported executable format', and in another (using sda instead of hd) it was 'error 23: error while parsing number'.

I don't know what other options to try.

I would GREATLY appreciate any help anyone can provide.  If I can clear this hurdle and the next one of finding a linux print driver for my HP PSC 1610 all-in-one I'll be completely up and running w/o any issues and grinning from ear to ear...

Help please... I'm soooooo close....

thanks,
Malac

---

### Post by sprucio on 2005-05-08
I'm not sure how GRUB handles SATA drives so that might be the first thing you want to check out.

---


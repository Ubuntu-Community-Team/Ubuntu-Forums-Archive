---
title: "2nd o/s not shown on splash screen"
date: 2007-06-29
forum: General Help
---

### Post by skeletor16940 on 2007-06-29
Greetings to all:-    This is my problem.  On my m/c i have three hard drives fitted.  One runs ubuntu, the other  two run Windows XP.  Previously, before some work carried out, when my ubuntu splash screen came up, it showed ubuntu, and the two windows xp o/s.  I had to re-install my version of windows on my first disc which was no problem.  I then re-installed ubuntu as my boot loader had disappeared when i formatted the disc.  No problem there.  However, when I rebooted finally, all that came up on the ubuntu splash screen was the ubuntu installation and the re-instated windows xp of mine.  The hard drive which my daughter was using i.e. the 2nd windows xp installation did not show.  what i would like to know is how I can get the 2nd version of windows xp recognised on the splash screen.  I can see the drive in windows, it can be seen in my ubuntu installation so I know it is there, I just can't boot into it from the ubuntu splash screen.  Any help very gratefully accepted.

---

### Post by eggdeng on 2007-06-29
If you take a look at your /boot/grub/menu.lst, you should see a section at the end along the lines of
```

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
This allows you to boot into your bootable XP partition by pointing to the boot sector of  (hd0,0) (counting from 0, first hard disk, second partition), where you have XP installed. You will need to add another similar section to be able to boot into your second XP. The only thing you will need to change is the disk it points to, presumably (hd1,0) ie second hard disk, first partition.

---


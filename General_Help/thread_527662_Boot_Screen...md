---
title: "Boot Screen.."
date: 2007-08-16
forum: General Help
---

### Post by ShakuganX on 2007-08-16
Hello, ever since i installed Ubuntu, my boot screen has changed to
[IMG]http://i7.photobucket.com/albums/y283/FantasyWarz/Untitled-1.jpg[/IMG]

I think this is called the Grub or something like that?
Would it be possible to change this back to the original windows boot screen?
If not, then..
I have windows XP and windows 98 installed on my computer, but this screen only shows XP.
I have to press enter when Windows XP is highlighted and that will take me to another screen that promotes me to boot from XP or 98.
Would it be possible to add windows 98 to the "grub" boot screen?
And would it be possible to change the order the items are listed? Windows 98 is still my main OS since my programs are only compatable with 98. I would like to move Ubuntu to the bottom, for now :)

Thanks guys :D

---

### Post by jamvegan on 2007-08-17
/boot/grub/menu.lst is the file that you need to edit.  You have a couple of options.  To simply make the Windows entry be the default OS that you boot into, you can change the line near the top of the file that currently reads:
> default         0
Your menu entries are numbered from the top of the file, starting with 0, so to make Windows the default, as the rest of the file now stands, you would change the 0 on the default line to 3.  Your boot menu would still look the same, except that Windows XP would be highlighted.  If you actually want Windows to appear at the top of the list, simply move its entry above the first Ubuntu entry in the menu.lst file.  Make sure you move the entire block of lines related to Windows if you do so, which probably looks something like:
> title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

You probably want to move the related comment lines (which start with #), as well.

As for including Windows 98 in the GRUB menu, perhaps someone else who has experience with it will chime in here, but I would guess that if it is on its own partition you could probably replicate the XP entry, changing the title and partition.  In the example above (hd0,0) represents the first partition on the first hard drive.  So, you might add a new entry to menu.lst that looks something like:
> title           Microsoft Windows 98
root            (hd0,1)
savedefault
makeactive
chainloader     +1

if Windows 98 were on the second partition of the first hard drive.

---

### Post by ShakuganX on 2007-08-17
Thanks for the help :)
I still need a bit of help for the windows 98 problem though.
I have 3 hdd's connected to my pc, 1 is for 98, 1 is for XP, and 1 is for Ubuntu..
So im guessing instead of 
```
title Microsoft Windows 98
root (hd0,1)
savedefault
makeactive
chainloader +1
```

i would use

```
title Microsoft Windows 98
root (hd1,0)
savedefault
makeactive
chainloader +1
```

?
Ill try it out when i get access to the computer again, but can someone confirm this is right?

---


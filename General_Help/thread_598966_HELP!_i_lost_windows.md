---
title: "HELP! i lost windows"
date: 2007-10-31
forum: General Help
---

### Post by notatoad on 2007-10-31
i installed xp yesterday, but i think it put the bootloader on my old hard drive.  today i installed ubuntu on a new partition on my drive, and erased the old drive. now windows won't load.  i put this:
```

title		Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader +1

```
in /boot/grub/menu.lst as suggested in [this]("http://ubuntuforums.org/showthread.php?t=331685") thread, but all it did was put garbage on the screen when i selected it.

any suggestions for getting windows back?

---

### Post by bhencetotozo on 2007-10-31
I had the same problem.. First do this:

get a windows xp cd .. when you get the blue installation screen, it will say R to go to the console.. so press  R

once your in the LIKE msdos window , tipe this :

fixmbr


then reboot the system. should work

---

### Post by louieb on 2007-10-31
Boot Ubuntu and open applications > accessories > terminal 
and post the output of ```
sudo fdisk -l
``` (lowercase L) 
This will list your partition table. Probably can help you with the GRUB menu entry after looking at that.

---

### Post by notatoad on 2007-10-31
will fixmbr restore my mbr to bypass grub and go straight into windows, though?

---

### Post by bhencetotozo on 2007-10-31
Yes i think so.

---

### Post by notatoad on 2007-10-31
ok, i tried fixmbr, then fixboot.  now i just get a message saying ntldr is missing.  any suggestions? EDIT: found this- [http://pcsupport.about.com/od/fixtheproblem/ht/ntldrntdetect.htm](http://pcsupport.about.com/od/fixtheproblem/ht/ntldrntdetect.htm)

if not, how do i restore grub?

---

### Post by inversekinetix on 2007-10-31
1 first put your xp disk in
2 choose R (repair)
3 type in fixmbr 
4 start windows
5 install wingrub using instructions here
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

6. when you boot you will get the windows boot loader with the option to START GRUB below the start XP option.  wingrub will find and load ubuntu for you.

---

### Post by notatoad on 2007-10-31
ok, the about.com instructions for restoring ntldr worked.

is there a way to reactivate the original grub, or is wingrub really the best way to go?

---

### Post by inversekinetix on 2007-11-01
I've only been using linux for a week, so I'm no guru.  I had the same problem as you and I solved it with wingrub, it works fine for me, just passing on what i know.

Maybe there is a way to fix grub, I can't understand why it doesn't work right in the first place, gave me loads of headaches.

---

### Post by notatoad on 2007-11-01
ok, i figured it out.  here's how i fixed my grub:

in livecd, open a terminal do sudo grub

then in the grub terminal enter the following:

root (hd0,0)     where hd0 is the hard disk and 0 is the partition
setup (hd0)
quit

and grub is working again!

thanks for all your help everybody.

---


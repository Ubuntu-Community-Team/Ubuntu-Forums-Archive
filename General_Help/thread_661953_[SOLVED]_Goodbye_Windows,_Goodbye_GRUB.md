---
title: "[SOLVED] Goodbye Windows, Goodbye GRUB?"
date: 2008-01-08
forum: General Help
---

### Post by scoalegil on 2008-01-08
I was an XP user who added Ubuntu to give it a shot.  After bouncing back and forth from Windows to Ubuntu for a few weeks, I realized there was nothing in Windows that I didn't have in Ubuntu except the ease of familiarity.  So I decided that a few weeks was enough, Ubuntu had won and I was simply going to get rid of Windows.

So I did, I repartitioned (a second hard drive) and formatted.
[I][B]
The final annoying reminder of Windows is its listing in the GRUB boot options.  

Can I simply go to  /boot/grub/menu.lst    and remove the Windows section?  Is there any reason to keep the boot menu with only 1 o/s installed?  If not, how do I get rid of it? [/B][/I]

I hope this makes sense and someone can help.  :)

---

### Post by p_quarles on 2008-01-08
You can just make the menu invisible. Here's how:
```
gksudo gedit /boot/grub/menu.lst
```
Uncomment or add a line that says this:
```
hiddenmenu
```
if you add it, it should directly follow the "timeout" line. You can also change the length of the timeout from the default 10 seconds to something more reasonable like 2 or 3.

---

### Post by scoalegil on 2008-01-08
Your suggestions worked perfectly.  Thanks!  

This is my first post to Ubuntu Forums, I am most pleased that this took 14minutes to resolve, thanks to the community.  I'm sure I'd have to sit on hold at least that long elsewhere.

---

### Post by Balazs_noob on 2008-01-08
luckily the community is very helpful
almost all issues take very little amount of time
to get solved..

Welcome to Ubuntu by the way ;)

---

### Post by p_quarles on 2008-01-08
No problem. Be sure to use the "thread tools" button at the top of the page to mark the thread "resolved." This will help others with similar questions find this thread in the future. 

FYI, you can still access the menu by pressing the escape key during the timeout period. Even though you've dropped Win, you still may need to choose the "recovery mode" or "memtest86" options at some point (but only if something goes wrong).

---


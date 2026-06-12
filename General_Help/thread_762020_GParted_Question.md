---
title: "GParted Question"
date: 2008-04-21
forum: General Help
---

### Post by emale07 on 2008-04-21
I have my macbook (3,1) partitioned with 60gb for OS X then 20gb for Ubuntu.  Did it with Boot Camp.

After fiddling for a few weeks, I've got everything stable and the way I like it and would like to enlarge the Ubuntu partition and move it to the front of the line.

Is that possible with GParted?

---

### Post by ibuclaw on 2008-04-21
Boot up the Computer into the Ubuntu LiveCD (You can only move unmounted partitions).

You should have no problems resizing all partitions.
You'll also have no problems moving them left or right of any empty space.

But the way that you describe it, you want to switch the partitions?

That I don't think is possible.

If you want to switch the order they appear in the boot menu.

Have a look at the menu file
```
 gedit /boot/grub/menu.lst 
```
And put the MacOSX lines behind Ubuntu's (Or Vice-Versa)

Regards
Iain

---

### Post by emale07 on 2008-04-21
That's helpful.  Thanks.

So I can run GParted from the LiveCD?

I currently have rEFIt installed.  Should I uninstall that?

---


---
title: "tty1-6: can't read font on terminal"
date: 2007-07-05
forum: General Help
---

### Post by Indefual on 2007-07-05
If it ctrl-alt-f1 or f2, f3, f4, f5, f6, it displays the terminal screen, and I can log in and do any commands, but I can't see what I'm doing.

The font is huge.  It starts off the left end of the screen and if the line is full it passes the right edge.  The effect is that I only get like 20 columns and 5 rows or something, and I can't read whats going on.  I can see the edge of the login prompt at the bottom of my screen.

If I login the cursor is below the displayable area of my screen.  if I type in enough commands it will start scrolling like normal, but I can't see my cursor unless I type in "clear".

Is there any way to fix this?

---

### Post by confused57 on 2007-07-05
> **Indefual said:**
> If it ctrl-alt-f1 or f2, f3, f4, f5, f6, it displays the terminal screen, and I can log in and do any commands, but I can't see what I'm doing.

The font is huge.  It starts off the left end of the screen and if the line is full it passes the right edge.  The effect is that I only get like 20 columns and 5 rows or something, and I can't read whats going on.  I can see the edge of the login prompt at the bottom of my screen.

If I login the cursor is below the displayable area of my screen.  if I type in enough commands it will start scrolling like normal, but I can't see my cursor unless I type in "clear".

Is there any way to fix this?
You could try adding "vga=791", without quotes to your kernel line in your menu.lst...open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
quit & save

Try adding vga=791 to the kernel line, reboot & try to access a console...may not work, but worth trying.

---

### Post by Qu4k3R on 2007-07-05
Do it works?

---

### Post by Indefual on 2007-07-08
No, it did not work.   But it led me to the solution.

I typed in what was suggested, but it said to me "Passed Invalid Mode" for my display information.  It then asked me to specify a valid mode from a list, I selected 0.

Once booted, I found that I could use tty1 and read the whole screen.

I edited the file and replaced the above with "vga=0" because 0 was the mode I selected.

Rebooted and everything looks fine.

Thanks!

---


---
title: "[SOLVED] Ubuntu hangs at Startup after kernel 19 update"
date: 2008-06-17
forum: General Help
---

### Post by irshadcharm on 2008-06-17
Hello guys ive updated the kernel today morning and all of a sudden ubuntu stops responding after reboot...i donno wat has gone wrong...? ive used a compizplugins script in which a particular plugins was not responding and i supppose due to this im not able to work in my ubuntu...any help wud be appreciated...waiting for a positive reply guys...

OS : Ubuntu Hardy...

Kernel: x.x.xx.19

---

### Post by Tom--d on 2008-06-17
When you boot, and see grub, press ESC.

Then chose a kernel which isnt -19 and see what happens then.

---

### Post by irshadcharm on 2008-06-17
ive already done that but i can see only the wallpaper and none of the panels are visible...im not able to go further...

---

### Post by irshadcharm on 2008-06-17
please help...waiting for a reply..

---

### Post by manfer on 2008-06-17
After grub, gdm is loaded.

In gdm you have an options button where you can select the type of session. Can you select gnome failsafe mode?

Enter system that way if you can and try to solve the compiz issue.

---

### Post by sports fan Matt on 2008-06-17
After the 19 kernel update, my volume control flat out failed--wouldnt even open.  I had to revert back to the 18 kernel to get it up and running. Im beginning to not upgrade kernels cause it starts to break things on my system

---

### Post by irshadcharm on 2008-06-17
> **manfer said:**
> After grub, gdm is loaded.

In gdm you have an options button where you can select the type of session. Can you select gnome failsafe mode?

Enter system that way if you can and try to solve the compiz issue.

u saved my life buddy...i tried with luck and and i was able to get into the failsafe gnome session and uninstalled the compiz plugin....whoooooooaaaaaaaaaaaa im back with my ubuntu....

---


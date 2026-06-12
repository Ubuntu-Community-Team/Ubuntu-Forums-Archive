---
title: "How do I boot into &quot;Safe Graphics Mode&quot;? (using wubi)"
date: 2007-05-09
forum: General Help
---

### Post by technologic on 2007-05-09
I installed ubuntu and since I'm using an ATI x800gto, my first boot just gave me a black screen. I think I need to boot into safe graphics mode then do some fiddling with my drivers. How do I get to Safe Graphics Mode? (I don't have a LiveCD.)

---

### Post by tuxcantfly on 2007-05-09
right after you select "ubuntu" from the menu, press ESC. It should show up a menu entry, then select the one that says "safe mode". If only 1 option is available, select that one, and press ESC immediately afterwards, and you should get the correct menu. If there's still only 1 option after the 2nd menu, press "e" to edit, and at the end of the line that says "kernel" remove "quiet" and "splash", add "single", press enter, and press b to boot.

Another way would just be to let it boot until it gets to the black screen, and press Ctrl-Alt-F1, or Ctrl-Alt-F2, login, enter "sudo -s" and it'll have the same result

---

### Post by GreeTufty on 2010-05-11
Hi,
   I'm having a similar (probably related) problem with ATI x200- everything was working until I installed the ATI drivers (for fireGL and radeon I think... Pretty sure x-series is a branch of radeon, perhaps I should have checked), and next time I booted, splash screen was fine, then when it got to login it did a change-of-graphics-mode thing and displayed garbage.
 
  Anyway, I'm going to try the above first and if it works, anyone who's having the same problem as me can know, otherwise I might need some more help.

---

### Post by dandnsmith on 2010-05-11
Using 'single' doesn't sound like the correct option to me - I believe that gives you single user mode (but cannot remember whether this is full graphics or just command line).

Looking at [the boot options](https://help.ubuntu.com/community/BootOptions) tells you the LiveCD method - so, not much help - but then goes on to a 'working installation', and you might get some mileage out of 'vga=771' as an option.

HTH

---

### Post by GreeTufty on 2010-05-12
Hi,
    Turns out this isn't my problem, but for users' information all tuxcantfly's suggestions result in a verbose boot, which ends in a variety of repair options including package repair and a command line interface.
    Having gone through this process of elimination it looks like I need a different thread...

---


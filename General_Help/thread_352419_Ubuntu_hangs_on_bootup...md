---
title: "Ubuntu hangs on bootup.."
date: 2007-02-03
forum: General Help
---

### Post by icehammer on 2007-02-03
Most of the time i choose Ubuntu from GRUB (i use XP too in a dual boot).. My screen would show, "Starting Up..", and then the ubuntu splash screen follows. The progress bar loads all the way, and then my system hangs!!! Keyboard lights stop responding (caps lock and all).. and then i gotta reboot infinite times, it still won't work. After i visit windows once, and then reboot and go into linux, it works perfectly fine, as if nothing happened!! why???

PS:
1. Ubuntu Edgy, XP Pro SP2
2. I've added a splash-background to GRUB.

please advise..

---

### Post by gradedcheese on 2007-02-04
The way I usually troubleshoot this stuff is to boot to runlevel 3 (multi-user, no graphical shell).  To do that I think you can enter the editor in grub and add a ' 3' to the end of the line that boots your kernel and proceed to boot.  Does it boot all the way to a shell that you can log in to?  What happens when you try to 'startx' manually then?  This way you'll also see any error messages that came up.

---


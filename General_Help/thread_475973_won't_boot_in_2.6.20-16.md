---
title: "won't boot in 2.6.20-16"
date: 2007-06-16
forum: General Help
---

### Post by KnowNothing on 2007-06-16
When my computer is booting up the OS at the top of the list is Ubuntu 2.6.20-16.  It will not boot if I leave that choice--I have to arrow down to 2.6.20-15 and then everything is fine.  For -16 I get the Ubuntu logo and one orange bar, then the screen goes blank and stays that way (this is the same thing that happens when I try to bring the computer out of hibernate).

I have to babysit the boot process and manually choose the older version.  Why are there two?  What is wrong with 2.6.20-16?  How can I fix this?

I'm not very savvy with Linux, by the way.  Thanks for any ideas or help.

---

### Post by floke on 2007-06-16
This happened to a lot of people. Big screw up. Just use 20-15 and forget it.

---

### Post by PilotJLR on 2007-06-16
> **KnowNothing said:**
> 
I have to babysit the boot process and manually choose the older version.  Why are there two?  What is wrong with 2.6.20-16?  How can I fix this?

You can make this the default behavior by modifying the "default" value in /boot/grub/menu.lst

Just note that the first entry is actually entry "zero"... so count up from there

---


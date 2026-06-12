---
title: "UBUNTU not working after trying to add monitor"
date: 2007-12-08
forum: General Help
---

### Post by mishranurag on 2007-12-08
Hi!

I have installed UBUNTU 7.10 on my Acer Extensa 4620Z. It works perfectly fine.  Once I tried adding second monitor to my laptop, and after I tried to restart X, it never started.

The computer stays at Black Screen with some script checking and [OK].  I have not been able to get into X. Could anybody please help or direct me to right forum?

Thanks
Anurag

---

### Post by geraldm on 2007-12-08
When X fails to start it should create an error log in the home directory, ~/.xsession-errors
Look in that file and try to adjust.
Without another plan, I would check file /etc/X11/xorg.conf and try to restore it to the way it was before adding the second monitor.  Then try to restart X,  and work any errors from the log.
Be sure to backup any files you change, so you have a way to restore them.

Gerald

---

### Post by UK-Wobbie on 2007-12-08
> **mishranurag said:**
> Hi!

I have installed UBUNTU 7.10 on my Acer Extensa 4620Z. It works perfectly fine.  Once I tried adding second monitor to my laptop, and after I tried to restart X, it never started.

The computer stays at Black Screen with some script checking and [OK].  I have not been able to get into X. Could anybody please help or direct me to right forum?

Thanks
Anurag

When you  tried adding second monitor did you reboot the pc? Or logout?
You got to reboot the pc and then at the login screen hit "CTRL-ALT-BACKSPACE"

Rebooting the PC helps on saving scripts. :)

May i ask what is your Video card? In your laptop?

Rob

---

### Post by Lostincyberspace on 2007-12-09
Linux lacks in this area a little you should really have both hoked up and reinstall to make it work simply.

---

### Post by mishranurag on 2007-12-09
Thanks for all the replies. I was able to restore my X back by using the command 

sudo dpkg-reconfigure -phigh xserver-xorg

I have yet to figure out how to add second monitor to this computer.

Anurag

---


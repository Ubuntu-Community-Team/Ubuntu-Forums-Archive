---
title: "Epson Printer Utilities"
date: 2008-05-10
forum: General Help
---

### Post by Paulo M. on 2008-05-10
Hello.....
I don't have much experience with ubuntu yet, but I've got a difficulty and need some help, please.
I'm running ubuntu 8.04 Hardy Heron (AMD64bit version) and have installed an Epson Stylus Photo R200 printer with CUPS+Gutenprint v5.0.2 Simplified drivers.
Needing to have access to ink levels I tried everything: Inkblot - never worked out; mtink - finally worked somtimes, not always, nozzle check unavailable and don't like interface; and at last, after searching a lot found Stylus Toolbox.
Installed Stylus Toolbox, but I've got no tray icon, nor option menus. The only way of making it work is in terminal "sudo stylus-toolbox", but, when I close terminal, GUI application closes too.
Please, any help, for making it work 100%?

Thanks in advance!

All my best

---

### Post by ildfroe on 2008-05-10
I don't know the program, but:
You could try to run the program via alt-f2 instead of the terminal.
There is also some command (or sign) to enter after the program name in the terminal which will leave the program running after the terminal closes, but I can't remember now :-(
You could also make a menu entry yourself via alacarte in system/preferences

---

### Post by The Cog on 2008-05-10
I haven't used it in recent versions, but when I had an Epson a while ago, I used a packaga called **mtink**. I also see there is a gnome package called **inkblot** which I shall try shortly.

---

### Post by ghost_ryder35 on 2008-05-10
have you added it to your sessions?
system, preferences, sessions

---

### Post by loell on 2008-05-10
from the main desktop, **right click** --> **create launcher**--> in the command text box type **gksu stylus-toolbox**.

---

### Post by Paulo M. on 2008-05-10
Thanks to all of you, but none of your replies solve my problem.
I've tried all of them, but still the same - no tray icon and no menu too... only by terminal!
About mtink and inkblot, I've tried them too, as I told before...
Any other suggestion?
Thanks anyway (of course)!

---


---
title: "Black screen with flashing white underscore"
date: 2012-12-07
forum: General Help
---

### Post by jackzta on 2012-12-07
Okay, so I have seen a few posts like this around but all of them say that you have to change the boot order and do a load of other things that I don't know how to do. 
My laptop was on the Windows 8 Consumer preview which ran out and I decided I wanted to switch to kubuntu. I put in the disc I made and tried the demo, then I wanted to install it so I clicked on the icon to do so and started the process. There were about ten different errors kept coming up but I just carried on anyway hoping that I would be able to get an update of some sort to fix the problems. 
In the end, the installer didn't work and whenever I turned my laptop off and on to switch back to Windows to find a solution, all that comes up is a black screen with a white flashing underscore.
I cant change the boot order or anything like that, Ive tried pressing all the F buttons and they do nothing. its just stuck. Does anyone know of a solution?

---

### Post by jackzta on 2012-12-07
It's on a Toshiba Satellite Pro L450-17L

---

### Post by jackzta on 2012-12-07
oops, I thought I couldnt change the boot order. turns out I can.
But what next? I've booted from the cd. but how do I get it to work now?

---

### Post by jackzta on 2012-12-07
Okay, this time around it only crashed :L

Thsi is what it says:

Installer Crashed
We're sorry; the installer crashed. please file a new bug report using the command 'ubuntu-bug ubiquity' in a terminal. this will gather information about your system and your installation process. the details will be sent to our bug tracker and a developer will attend to the problem as soon as
Traceback (most recent call last)
File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 957, in
on_next_clicked
self.dbfilter.ok_handler()
file "usr/lib/ubiquity/plugins/ubi-usersetup.py", line 806, in ok handler self.ui.hostname_error(make_error_string(self.controller, errors))
AttributeError: 'Page' object has no attribute 'controller'

---


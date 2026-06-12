---
title: "t60 with feisty no longer resumes from suspend"
date: 2007-05-11
forum: General Help
---

### Post by insert_name_here on 2007-05-11
My Lenovo t60 just stopped resuming from suspend.  It (usually) suspends correctly, but when I try to resume it, it gives me some sort of colorful screen with moving lines.  Then, the colorful stuff goes away, and leaves me with a black screen, from which I cannot wake up my computer.

This occurred sometime around when I used 'sudo dpkg-reconfigure gnome-applets' to allow me to set my cpu frequency from the gnome-applet.  However, I tried returning that setting to its previous state, which didn't help.

Ideas?  Commiseration?

---

### Post by philhinz on 2007-06-24
I have the same problem.  It used to suspend fine using Fn+F4 or suspend, but broke at some point.  I am using Feisty.  I did not note carefully when it broke.  After resume it shows a light blue screen with flickering horizontal lines for a few seconds.  It then goes blank and requires a hard reboot.

One oddity I found is that if I logout and restart the X server (Ctrl+Alt+backspace) I can then choose suspend and it will resume fine.  I suspect it is a problem with something I installed recently . . .

---

### Post by insert_name_here on 2007-06-24
I *think* I fixed mine just by re-installing feisty.

---

### Post by philhinz on 2007-07-05
I did a fresh install of 7.04 and still have the problem that I get a blank screen after resuming from suspend.

---

### Post by philhinz on 2007-07-05
Okay, I finally figured out my problem.

I had been playing around with installing Beryl and never got it working correctly.  I had some leftover configuration files in my home directory (.beryl and some other folders).  Once I deleted all of the configuration files associated with beryl I was again able to suspend and resume.

The reason this persisted after a fresh install was that I foolishly copied over my configuration files from my previous installation.

---


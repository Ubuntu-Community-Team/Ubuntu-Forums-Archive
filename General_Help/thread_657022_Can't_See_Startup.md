---
title: "Can't See Startup"
date: 2008-01-03
forum: General Help
---

### Post by sekinto on 2008-01-03
This happened when I was using Ubuntu (I just installed Xubuntu because Ubuntu was to slow and it is still happening).

Anyway, when my computer starts up it shows NOTHING between the bootloader screen and login screen, no progress bar, no text, nothing. It really bothers me. Is there any way to fix this?

---

### Post by Borbus on 2008-01-03
What GPU do you have? 8800GT by any chance?

---

### Post by sekinto on 2008-01-03
No, it is a Radeon XPRESS 200M 5955, and personally... I hate it.

---

### Post by Borbus on 2008-01-03
Hmm.. Ok... well my new 8800GT does the same thing. My monitor actually switches itself off during the part where the ubuntu boot screen should be. I'd rather just change it to a classic linux text loader that actually works.

---

### Post by sekinto on 2008-01-03
The funny thing is it works when using the LIVE CD. What the hell?

Anyway, my monitor stays on and just doesn't show anything, then a few seconds before the login screen it switches off for a few seconds and then back on.

---

### Post by alqualond on 2008-01-03
I had a similar problem with my laptop (HP dv6541, with an NVIDIA graphics card.) I didn't find a solution that would show the progress bar etc, but I disabled the splash screen during startup and shutdown, and now I see text output and it loads faster. 

If that's the problem you're having, and you don't mind not seeing the graphics, you need to edit one of GRUB's files: /boot/grub/menu.lst . Scroll down to where it lists the different loading options (in my file, it's right after: ###end default options###). Find the entry for the option you choose, then, at the "kernel" line, remove "splash". 
Make sure you backup the file before editing it!

Hope this works!

---


---
title: "How to edit the screensaver file"
date: 2008-02-21
forum: General Help
---

### Post by lsutiger on 2008-02-21
The problem is that everytime I run the gnome-screensaver-preferencess, it crashes X. 

I have fixed the issue of the screen going blank before the screensaver starts, but now the screensaver stays on indefinitely. I am attching my config file for screensaver.

I would like the screensaver to start at 20 minutes idle and go into power management mode after 1 hour.

I am not sure what the mtime variable is, and I am scared to fool with it.

Could someone help me out?

---

### Post by lsutiger on 2008-02-24
I changed the line ```
<stringvalue>screensavers-flipscreen3d</stringvalue>
``` to ```
<stringvalue>none</stringvalue>
``` and that stopped the screensaver preferences from crashing.

But power management does not work....

---


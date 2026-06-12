---
title: "Problem with window manager?"
date: 2006-10-29
forum: General Help
---

### Post by domf on 2006-10-29
Following an upgrade I've a few problems I'm working through (at least I've got an Xserver now!).

The current problem is that although my Xserver is starting fine and I can log in as soon as I open any window it is pinned to the top left hand corner and cannot be moved - this happens for all windows.

How do I troubleshoot/resolve this.

Thanks


Dom

---

### Post by .t. on 2006-10-29
Get to a terminal (Ctrl+Alt+F1) and log in there. Run "DISPLAY=:0 metacity --replace &". Go back to your X session (Ctrl+Alt+F1). Does that help?

---

### Post by domf on 2006-10-29
Yes - I ran this in a terminal window  and it works until I log back out & in.  Does this mean that Metacity is not starting/crashing?


Dom

---

### Post by domf on 2006-10-30
<bump>

If anybody had any ideas I'd appreciate some help - I have a workaround but having to run progs from the command line every time you login is hardly in the Ubuntu ethos!


Dom

---


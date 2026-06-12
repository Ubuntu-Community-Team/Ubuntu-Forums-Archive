---
title: "Paper Size"
date: 2006-07-24
forum: General Help
---

### Post by _simon_ on 2006-07-24
No matter what application I use or how many times I change it from US Legal to A4 it refuses to save it.

Is there anyway to default to A4 rather than US Legal?

This is also the case on my partners machine.

---

### Post by ajgreeny on 2006-07-24
You ned to do this in your printer setup in order to keep the paper size you want as your default.  Reinstall the printer or go to the gnome printer manager (I use KDE so am not sure how to do it in gnome, but it must be there somewhere) and change paper size to A4.  That should do it.

---

### Post by _simon_ on 2006-07-24
Unfortunately it is already set to A4 in the printer properties of printer manager.

Any other ideas? :confused:

---

### Post by dspivey on 2006-07-24
use the CUPS web interface ([http://localhost:631](http://localhost:631) in your browser).  go to administration and change the default paper size for your printer.

---

### Post by _simon_ on 2006-07-24
it's set to A4 in there as well!

If I open for example - Gedit or Writer and go to print then check the paper type before printing it says US Legal and if i accidently print without changing it, my printer moans at me that it's US legal and not A4.

---

### Post by ajgreeny on 2006-07-24
In KDE, if you go to the Date & Time Format of the clock in the panel, there is a tab named other that gives paper size.  I don't know if there is a similar tab or anything available in gnome, but it's worth a look.

---

### Post by dspivey on 2006-07-24
delete your printer from System>Administration>Printing and reinstall it using the CUPS web interface.  Print a test page from the CUPS web interface before trying from any applications.

---


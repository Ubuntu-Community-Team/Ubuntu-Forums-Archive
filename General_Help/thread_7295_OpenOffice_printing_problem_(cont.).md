---
title: "OpenOffice printing problem (cont.)"
date: 2004-12-05
forum: General Help
---

### Post by bogl on 2004-12-05
I have followed this thread:

[http://www.ubuntuforums.org/showthread.php?t=2205&highlight=oo+printer](http://www.ubuntuforums.org/showthread.php?t=2205&highlight=oo+printer)

and followed through the associated bugzilla:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=1925](https://bugzilla.ubuntu.com/show_bug.cgi?id=1925) 

...and yet OpenOffice still will not print.  Have tried a reinstall of OO to no avail.

Is there another fix??

---

### Post by fmou on 2004-12-07
I've had the same problem....
I re-installed Ubuntu without connecting the printer, and once Ubuntu installed, I've connected the printer. And now I can print with OOo and other software.
For sure, that's certainly not a good way to solve the problem, but it works!

---

### Post by bogl on 2004-12-07
Not keen on reinstalling I must say, I've just got to the point of everything being tweaked to my satisfaction.

However, at least I can export as PDF & print from there.

Be nice to do it direct though...

bogl

---

### Post by Sorin Paliga on 2004-12-08
Is there another fix??[/QUOTE]

OO puts a lot of problems in print, among others - if diacritical marks (I'm Romanian) are used, the basic font (Times family) is substituted by a Swiss font, even if settings are (seem?) OK. Curiously enough, OO in Ubuntu is the ONLY which does NOT have this problem (it is usual in Mandrake, SuSE...).
Another problem is indeed to not print at all. Well, cannot figure out your settings, but check first if printer is correctly detected, if not - add it manually (I did this earlier today, was not automatically recongnised). Print a test page, if OK, print in another app, say Abiword (you have to add it, not installed by default)… or choose another app. If there is OK, and OO still does not print, well: check again if paper type (A4 or else) is correctly set… even if A4 or Letter seem to not be essential, it may happen.
If printing in OO is the ONLY which puts problems, well, it begins to be strange. In other linux distros, there is a specific setting labelled 'OO printer settings' (or something like this), which seems generally useless; anyway it is absent in Ubuntu.
Was this useful? If not...

---

### Post by bogl on 2004-12-08
I'm afraid this is an OO-only issue.  Printer works excellently in every other respect.

Thnaks for the thought, though!  Helpful to others I'm sure.

Ubuntu developers: is there a plan or a long-term fix to this problem???

bogl

---


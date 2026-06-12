---
title: "Trouble importing true type fonts"
date: 2006-12-25
forum: General Help
---

### Post by Baasha on 2006-12-25
Hi,
I am running Ubuntu Edgy and I can't import certain fonts into my system.  I can view the fonts with the Gnome font viewer, but for some reason when I try to drag and drop them into the fonts:/// folder they won't go.  The fonts are Palantino and Tahoma, among others.  Can someone give me some clues as to why they won't import?

TIA,
Bob

---

### Post by bodhi.zazen on 2006-12-25
See if this helps:

[http://doc.gwos.org/index.php/Microsoft_Fonts](http://doc.gwos.org/index.php/Microsoft_Fonts)

---

### Post by Baasha on 2006-12-25
No, that doesn't cover my problem.  I already have the MS core fonts installed.  It is just that I can't import some other fonts into the fonts:/// folder.  I can load and see them fine with the Gnome Font Viewer, so I am assuming that it isn't a Linux compatibility problem.  These are well known and common fonts (Palantino, Tahoma) so I can't figure out what the problem could be.  Any other ideas?

Bob

---

### Post by bodhi.zazen on 2006-12-25
Try running as root:

gksudo nautilus

Then import

---

### Post by spockrock on 2006-12-25
I believe there is a .font folder in your home directory....... did you try that??

---

### Post by Baasha on 2006-12-26
Yes, I knew about that directory, and I had already tried that.  As far as I know the fonts:/// location in Nautilus is just a sym link to that .fonts directory.  Bodhi had the correct answer: You have to use sudo to do the import.  The help pages don't mention that.

Bob

---


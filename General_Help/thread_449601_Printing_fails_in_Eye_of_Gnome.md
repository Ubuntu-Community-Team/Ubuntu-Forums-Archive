---
title: "Printing fails in Eye of Gnome"
date: 2007-05-20
forum: General Help
---

### Post by mgmiller on 2007-05-20
I am Running Feisty, upgraded from Edgy.

I usually print from Open Office or Gimp or even Picasa without problems.  I just tried to print a simple .png after opening it in eye of gnome (image viewer).  I scaled the image and clicked print and after a few seconds got the error message: Error Printing Too many failed attempts.  I then opened the image in gimp, scaled it and printed without issues.  Tried again in EOG with and without scaling and got the same error message.  I had never tried to print from there before, it has a nice interface for doing simple things and it is quick to load, etc.  

Any thoughts on what is going on here?  A search of the forums with the error message didn't produce anything relevant.

Edit:
I just encountered the same error trying to print an e-mail from evolution.  I went to ~/.gnome2/evince and found the file ev-print-config.xml.  It only contains a printer I no longer use.  I renamed the file to ev-print-config-bad.xml and now evolution printed  ok 1 time and then started giving me the same error.  I still get the same error printing from eog.

---

### Post by bajeli on 2007-09-18
> **mgmiller said:**
> I am Running Feisty, upgraded from Edgy.

I usually print from Open Office or Gimp or even Picasa without problems.  I just tried to print a simple .png after opening it in eye of gnome (image viewer).  I scaled the image and clicked print and after a few seconds got the error message: Error Printing Too many failed attempts.  I then opened the image in gimp, scaled it and printed without issues.  Tried again in EOG with and without scaling and got the same error message.  I had never tried to print from there before, it has a nice interface for doing simple things and it is quick to load, etc.  

Any thoughts on what is going on here?  A search of the forums with the error message didn't produce anything relevant.

Edit:
I just encountered the same error trying to print an e-mail from evolution.  I went to ~/.gnome2/evince and found the file ev-print-config.xml.  It only contains a printer I no longer use.  I renamed the file to ev-print-config-bad.xml and now evolution printed  ok 1 time and then started giving me the same error.  I still get the same error printing from eog.

I have the same problem I cannot print from eye of gnome, although I print without problem using firefox, OpenOffice or Gimp.
I noticed that Frefox, OpenOffice and Gimp refer to the printer using "CUPS/printername" in the printer chooser dialog,
 in opposition EOG refers to the printer using "printername" without CUPS prefix.
Could it be the problem?

---

### Post by calinb on 2007-10-31
Looks like a bug to me!  A very inefficient work-around is to close the Eye of GNOME ap and relaunch it for every print job.  And don't try to queue more than one job to CUPS.   :(

Anyone found a fix yet?

-Cal

---


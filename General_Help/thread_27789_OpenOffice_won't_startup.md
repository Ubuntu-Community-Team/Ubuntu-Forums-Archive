---
title: "OpenOffice won't startup"
date: 2005-04-17
forum: General Help
---

### Post by ~WhitE-RaveN~ on 2005-04-17
I just installed the latest version of Ubuntu on my Toshiba Satellite M30 laptop.  I was very impressed with it at first.  I got my wifi card working (not on startup, but that's another story) in almost no time.  I started working on something today in OpenOffice Writer.  I saved the document and shutdown my laptop.  Later, when I wanted to work on it again, OpenOffice kept crashing.  I tried reinstalling the OpenOffice packages, but no luck.

I ran OpenOffice alone, and it came up just fine, but once I tried to open something wordprocessed, it broke.  I get the splashscreen, and the loading bar fills itself up, and then nothing happens.  If I put other windows in front of the OpenOffice window, and move them away, I get a nice white spot where the windows overlaped (something has frozen).

Any suggestions?

Thanks

---

### Post by Knome_fan on 2005-04-18
Did you try to start it from a terminal (with oowriter), to see if you get any error-messages?
You could also try to move the .openoffice away to for example .openoffice_bak and see if that helps. If you do the latter you'll also have to comment out the relevant entry in .sversionrc iirc.

---

### Post by ~WhitE-RaveN~ on 2005-04-18
Thanks for the tip.

When It tried again today, I recieved an error message stating that according to "~/.openoffice/.lock", another instance of OpenOffice was accessing my user information, and may cause a conflict.  I knew this wasn't the case, so I clicked "Yes" to continue anyway.  Although office didn't load by force, after deleting the .lock file, it worked like a charm.

Thanks again.

---


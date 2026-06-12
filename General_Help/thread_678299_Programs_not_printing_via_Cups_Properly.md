---
title: "Programs not printing via Cups Properly"
date: 2008-01-25
forum: General Help
---

### Post by hoggbottom59 on 2008-01-25
My printing to my network printer from programs is no longer working.
I can print a Test Page ok from the printer dialog box.

It seems there is a problem with the programs printing to CUPS but I can't work out what to do.
There are a few errors in the cup error log about not having authorisation for the userid and also no ticket cache.

Using Ubuntu 7.10 to a linkstation NAS driver using it's printer server to print.

I've tried complete removal and reinstalling but this hasn't helped.


Thanks
Leon.

---

### Post by pneaveill on 2008-01-25
Sorry, but as I read through this, am seeing more questions than answers.  

Might be helpful to know which printer it is that you are dealing with. What other steps have you taken to remedy the problem?  Has it ever worked on this or other accounts on that machine? Can other machines print to the printer?

Are you absolutely certain that you have the exact right driver for the printer?  As you might be aware, there are several options for certain printers. Some of those work better under certain conditions and not others.

Hope some of this might help.

---

### Post by kraymore on 2008-01-25
i cannot print over the network using CUPS either.  there was a bug in a update released about a week ago that caused problems.  i believe avahi is the culprint.  i'm hoping a bug fix of this will be released soon.

---

### Post by hoggbottom59 on 2008-01-26
Sorry I probably didn't make it clear in the first post.

I just went to print to a printer that has worked for ages. 
I haven't printed for a while and hadn't changed any settings. I've tried reinstalling the printer several times but it seems to be a break between programs sending to CUPs properly.

If it was a dubious bug fix does anyone know how to roll back Avahi to test this theory?


Yours
Leon.

---


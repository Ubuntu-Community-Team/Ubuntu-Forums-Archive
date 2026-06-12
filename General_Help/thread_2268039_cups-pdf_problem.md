---
title: "cups-pdf problem"
date: 2015-03-05
forum: General Help
---

### Post by Claudia_Zeiler on 2015-03-05
I had the same problem of not being able to print using Document Viewer.   I was solving the problem by printing with Gnome Print Preview.  Before I realized that the problem was Document Viewer  newbie style * blindly followed the instructions "sudo apt-get install cups-pdf".  Now I can't print ANYTHING!  What have I done to myself?  How do I back myself out of this situation?  I don't even see the PDF folder  in my home folder that print files are supposed to now appear in.

TYIA for any help you can give.

---

### Post by Portaro on 2015-03-05
Hello claudia and welcome , You dont have the option to print to file? on your aplications or browser?

to go back you need to purge & remove cups-pdf , but I think your problem is not cups, maybe is your aplication 
, try other for example - evince, xpdf , if is a pdf file?

for pictures use gimp and for odt libreoffice etc.

All you need is to see if on your aplication appear this -

File -> Print-> prin to (a file) to a printer...

If you dont have this on any file viewer then there are a problem with (print to file type)

Ithink the cups pdf config is on -> ** /etc/cups/cupsd.conf **

**Be happy with GNU/Linux.**

---

### Post by Claudia_Zeiler on 2015-03-06
Thank you for replying to my problem so promptly.  I wasn't able to print from any program.  Finally I saw somewhere that the printer was stopped and rejecting jobs.  I went to 
[http://127.0.0.1:631](http://127.0.0.1:631) in the printer tab.  After various tabs I deleted the printer entirely and then disconnected it, turned it off and on, and then reconnected and re-added the printer.  I am now back to normal and printing again.

I am reciting this whole long explanation in hopes that it is helpful for someone else.  

Thank you again for your reply.
Claudia

---

### Post by Mike_Walsh on 2015-03-06
Couldn't agree more.

I discovered VERY early on that deleting a printer, and then re-adding it, often cures a whole raft of related problems...

And in all honesty, if you re-install via the CUPS web interface, on 'http://localhost:631', it gives you a far greater degree of control, too.


Regards,

Mike. :)

---


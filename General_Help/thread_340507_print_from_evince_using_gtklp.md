---
title: "print from evince using gtklp?"
date: 2007-01-17
forum: General Help
---

### Post by madmaxx on 2007-01-17
Hi

How can I get evince to use gtklp for printing instead of the rather limited standard printing dialog?

Related question: Why is gtklp -- a really mature and useful tool IMO -- not part of the ubuntu standard installation?

Thanks for your help!
madmaxx

---

### Post by bmt on 2007-02-05
Well, I can't answer your second question.  I wish I knew!

To get Evince to print to gtklp:

In the Evince print dialog, select 'Generic Postscript' as the printer.

Click on 'Location' and select 'Custom', then change the printer command in the text box to the right of the location button ('lpr' by default) to
```
gtklp
```
Click on the 'Print' button and gtklp will open.  Continue to select printer and options as required.

As this is two weeks after your initial post, you've probably already worked it out for yourself ... ;-)

---

### Post by madmaxx on 2007-02-06
Thanks, bmt. Never mind about the two weeks... I would not have found it because it does not seem to be there! Besides the real printers, there is only a "print to file" to choose, but no generic PS printer... Any ideas why that could be? :-k
thx, madmaxx

---

### Post by bmt on 2007-02-06
Okay -- good excuse!

I should point out that I'm talking about Evince v0.5.2 (from the Dapper repos.) on Dapper.

In the Print dialog window, there are the printers according to CUPS, plus two other options: 'Create a PDF document' and 'Generic Postscript'.  Looking at the Evince help pages (in the Gnome help, not online) the print menu is quite different again -- it talks of completely different options.

Over time, I have installed and removed a few print-related options, but I'm not aware of anything that could have added (but not removed) the PDF and PS options.  Try forcing the Dapper version, if you're on a later Ubuntu?

Added:  [This page]("http://people.redhat.com/~alexl/print_dialogs/Linux/linux.html") shows the default libgnomeprintui dialog -- it's the same as mine (scroll down past the Firefox and Gimp entries).

---

### Post by madmaxx on 2007-02-06
Thanks for the screenshot!
I am on Edgy Eft (evince 0.6.1). Interestingly, the print dialog my "gedit" looks exactly as the one in the link you provided: "generic postscript" and "print to file" are there. But, alas, in evince I can only see the "print to file" option... *puzzled* 
Any more ideas? TIA, madmaxx

---

### Post by bmt on 2007-02-07
Since I started looking closely at printing from Gnome applications (after paper size problems with gLabels), I came to realise that the whole printing thing is a bit of a hotch-potch.  There are several possible routes from application to printer, none of which is perfect and parts of which are no longer even maintained.

As for your Evince issue, I would suggest trying an earlier version (perhaps from the Dapper repos.).  It would not be difficult to change back again in the event of other problems.  For that matter, try reinstalling your existing version.

If you can't resolve it, then certainly raise a bug report.

Good luck!

---


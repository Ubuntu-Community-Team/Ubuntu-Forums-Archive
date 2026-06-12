---
title: "More Robust PDF Programs?"
date: 2007-03-26
forum: General Help
---

### Post by SavantEdge on 2007-03-26
I'm wondering if there's a good PDF program that I just haven't found, because I've not been well satisfied by the current offerings.

I was looking for a good print-to-pdf solution, and I stumbled across CUPS-PDF.  It's okay (the format looks okay, anyways), but it has some serious problems: namely, you can't copy-paste text from the PDFs it generates.  (I sent it over to a friend on Windows to see if they could; they couldn't.)  Some programs, like OpenOffice.org have their own PDF functionality built in; why can't we get a nice PDF virtual printer to use in all programs (most of all: firefox).

Evince is okay for a quick reader, but if you want to do anything besides reading, it can't do it.  (For example, save a page separately, or delete a page, or access the permissions/restrictions on a PDF.

Is there a program that has more functionality regarding PDFs other than CUPS-PDF and Evince?

---

### Post by Jussi Kukkonen on 2007-03-26
If you think about the technical details involved, it becomes quite clear why you didn't find what you were looking for... A general print-to-pdf function that preserved text as text would have to understand and render every possible text format ever invented -- I doubt we are going to see that happen.

Even a text preserving html-to-pdf converter would be a huge task, probably not worth the effort (considering that html is already an open format suitable for most things this pdf-export could be used for).

---

### Post by SavantEdge on 2007-03-26
Well...I hate to resort to this argument, but... Windows has it.  =\

But fine, letting that slide, what about a program with stronger PDF editing facilities?

---

### Post by mexlinux on 2007-03-27
> **SavantEdge said:**
> I'm wondering if there's a good PDF program that I just haven't found, because I've not been well satisfied by the current offerings.
.....
.....
  Some programs, like OpenOffice.org have their own PDF functionality built in; why can't we get a nice PDF virtual printer to use in all programs (most of all: firefox).

We do!
It's part of KDE: kprint 
You can use it to print from any program (even from gnome).
And the text is selectable copyable, etc.

---

### Post by Jussi Kukkonen on 2007-03-27
Ok, I'll have to believe you guys (little experience from KDE, even less from Windows), I'm still left wondering if it really is generic -- I bet it's not (just well supported)... I'll have  to test this some day.

SavantEdge, kprint is not a package but if you want to test it on Gnome, it'll *probably* appear on kdelibs installation. I suggest you use aptitude to install stuff like that: if you ever remove kdelibs, aptitude will remember which libraries it brought with it, and uninstall those too. If you use other methods you'll be left with a lot of unnecessary stuff on th machine.

---

### Post by SavantEdge on 2007-03-27
I noticed kprint in my search prior to this, but I didn't know I could use it in gnome...how would I set that up?  (I couldn't find any tutorials on that, just a bare passing mention...)

---

### Post by mexlinux on 2007-03-27
kprint can be used to print from stdin.
In other words, simply specify 'kprint' as the printer command (instead of 'lp' or whatever is used from firefox or anyother app.

---


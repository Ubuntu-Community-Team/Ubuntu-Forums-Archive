---
title: "Scanner on Print Server"
date: 2007-06-17
forum: General Help
---

### Post by shane_on_u on 2007-06-17
I just purchased a Samsung SCX-4200 multi-function printer. The printer is connected to a Linksys print server. I've installed the Unified Linux Driver from Samsung and I have the printer printing without issue.

The only thing I need to figure out is how to access the scanner via the print server? I've been seaching for info on this all day but I haven't found anything to point me in the right direction. Does anyone have any experience with this or any info that could at least help me get started? Your help is much appreciated.

Shane

---

### Post by llamakc on 2007-06-17
I use XSane to scan with my Brother all-in-one with no problem.

---

### Post by shane_on_u on 2007-06-17
I can't even start XSane because my scanner isn't detected. Is your Brother all-in-one on a print server?

---

### Post by llamakc on 2007-06-17
I'm an idiot: I didn't catch that part of your post. I used Brother's scanning .deb to set up XSane.

I once had it set up w/o the Brother .deb, but I forget what it was I did in the CUPS web interface to get it set up. I'll have to look through my notes. I know it was something as simple as I entered something in the commandline, got an output and used that to set up the printer via the CUPS web interface. I'm googling but I can't find the answer yet.

Okay, I remember now: I used "hp-makeuri" from the hplip package (even though I didn't have any particular HP product installed).

Sorry for the rambling. It's Father's Day and I'm drunk.

---

### Post by llamakc on 2007-06-17
I tried to duplicate my stuff upstairs. I lied. That worked for my last all-in-one. For my current machine I had to use Brother's stuff. Sorry to waste your time.

---

### Post by shane_on_u on 2007-06-17
Thanks for the quick reply. I came across hp-makeuri while I was searching earlier but dismissed it as my printer isn't an HP. I just gave it a try (hp-makeuri 192.168.0.100) and I'm getting the following error:

"error: Device not found"

I'm about ready to give up :P Maybe I should just return the printer and go with a Brother instead. I saw instructions for making the scanner for that work on a print server somewhere I think.

Oh and happy fathers day!

---

### Post by fatbuttlarry on 2008-01-05
For the record, my print server was hooked up to an HP printer, but doesn't list any scanning support.   Unfortunate, because it renders the scanning functions useless unless its plugged in USB.  Cheers.

-Tres

---


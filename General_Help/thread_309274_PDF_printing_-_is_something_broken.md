---
title: "PDF printing - is something broken?"
date: 2006-11-29
forum: General Help
---

### Post by cogitordi on 2006-11-29
Using Drake and Eft. I have a print server on a network. I can print to this print server from OpenOffice, Firefox, Gedit, and so on. I have a document that I created using OpenOffice. I can print the document. I exported the document to PDF. I can't print the PDF! I can print other PDFs.

I can also print the offending PDF from an OS X box on my network. 

I conclude that the problem is not my network, it's not my print server, it's not my printer, and it's not the PDF. 

I'm speculating that Evince is encountering something in the PDF that causes spooling to abort. Any suggestions, folks?

---

### Post by lhtown on 2006-11-29
I haven't had any problems myself. You might try saving it with different options enabled and disabled. If you have security enabled, I would try that first.

If you created the file on the same machine you are printing it from, it shouldn't be a fonts issue.

It sounds like you have encountered a bug in Evince. At the very least, it should be throwing errors saying that what you are trying to do is beyond its feature set.

You might try recreating the pdf on a different machine to see if that copy works. Also, you might try leaving out some of the stuff in you pdf or creating an entirely different document in OpenOffice.org on the same machine to see if that works.

---

### Post by heng on 2006-12-11
I seem to have hit this bug too. Not sure what is causing it. I'll look into it.

---

### Post by jonah1980 on 2006-12-11
printing problems seem to always be changing for me. the whole gnome print method needs serious work. some programs rely on your saved default settings and can't be change, some progs print half off the sheet, some stuff is awful colours etc. i use a turboprint ppd which seems fine on some apps and test prints etc but not others.

all apps should offer a basic print dialog where you can set quality, paper type, portrait/landscape etc so you're not always left guessing. i know it's not just gnome and often kde and gtk apps are to blame for causing these probs too.

i hope all desktops and linux apps can work to a more generic and standard print method in future...

as i'm a professional photographer and work also in graphic design, i can't afford to be messing around trying to print a pdf for a day.

---


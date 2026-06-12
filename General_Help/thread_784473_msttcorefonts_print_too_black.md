---
title: "msttcorefonts print too black"
date: 2008-05-06
forum: General Help
---

### Post by Tim Watson on 2008-05-06
I've installed msttcorefonts using synaptic on a fresh installation of hardy. The fonts look fine in OpenOffice but when I print them on my HP  Deskjet 6940 they come out too black (as though the text has been set to bold). Other fonts are fine when printed. The same problem is replicated on my office machine at work (different PC hardware, same printer model, same installation and configuration settings).

I haven't tweaked any printer settings and everything else appears fine.

Is there a font weight setting problem in the ttf files (I'm no expert on the file format and quite how it interacts with the printing system)? Is anyone else having similar problems? Can anyone suggest a fix?

Thanks,

Tim.

---

### Post by Tim Watson on 2008-05-08
Is this just me? Is anyone else finding that when printing Times Roman, Georgia, Arial etc. they are too black (they look like they're bold when printed but they're fine on the screen) but non-msttcorefonts are fine?

Any reply would be appreciated as it will help narrow my search for a solution.

Thanks,

Tim.

---

### Post by Tim Watson on 2008-05-09
I've narrowed the problem to OpenOffice - a test document that looks fine on the screen and that prints out looking too black/bold, prints fine when exported as a pdf and printed via evince.

Tim.

---

### Post by yaknowwat on 2008-05-09
It's probably because in linux the fonts you see are closer to how they are printed out then on windows where in windows they are made to be clearer on screen of course this messes up with direct printing.

---

### Post by Tim Watson on 2008-05-10
Thanks, yaknowwat. However, the printout is truly dreadful (imagine a sort of double bold making the text so black and thick that it's almost shouting at you, even in 10 point!). Never willingly using Windows (even my work machines are linux only), I wouldn't know how they look when printed with inferior operating systems :-)

The convert to pdf then print workaround will do for now but at some point I hope that I can work out the root cause. OpenOffice does its own font rendering, from what I have read so far, and that seems to be the main cause of the problem. I'd leave a bug report in the OpenOffice issue tracker but you have to register to do so.

All the best,

Tim.

---

### Post by jpneal on 2008-05-13
I have the same problem with an HP Officejet 6310 printer.

---

### Post by jpneal on 2008-06-03
Still having the same problem. 

PDFs are printing OK. OpenOffice documents are slightly too bold. It makes the documents look "heavy".

---

### Post by smain on 2008-09-25
I know this thread is old, but i'll just bump it because I'm having the same problem, so I hoped somebody had discovered a solution :D...

---


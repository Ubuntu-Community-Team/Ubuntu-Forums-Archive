---
title: "Printing PDF trouble..."
date: 2007-10-30
forum: General Help
---

### Post by fcoster on 2007-10-30
I just did a fresh install of Gutsy on my computer which had previously been running Dapper (it's been awhile I know). I've had some trouble with my formerly problem-free HP LaserJet 6.

I can print a test page; and I can print from OpenOffice. But when I try to print a PDF file, nothing happens. Any ideas?

Thanks,

fcoster

---

### Post by fazavon on 2007-10-30
Check your home dir, Gusty makes a PDF folder and puts it there, you should have Print to PDF files there

---

### Post by fcoster on 2007-10-30
Thanks; I'm not trying to print TO pdf; I'm just trying to print a PDF. I open the file in Evince; but when I try to print nothing happens.

-fcoster

---

### Post by nikkkko on 2007-10-31
I have the identical problem in that my hp laserjet was recognised immediately, test pages print as do other applications, but not from Evince.  No problem, I downloaded Acroread from the Medibuntu repository and that prints fine.  (Acroread is a superior program in any event).

---

### Post by tubasoldier on 2007-10-31
> (Acroread is a superior program in any event).

Let's just call that a matter of opinion.

I had the same issue when I had a really old HP LaserJet 4. KPDF worked well for me.

---

### Post by nikkkko on 2007-10-31
> (Acroread is a superior program in any event).
IMHO - I've been using Kubuntu up until now and Acroread was the only program which showed transparencies and colours properly for me.

Anyway, I've been trying Ubuntu, (upgrade to gutsy), for two days and still haven't resolved my printing problem, despite my last post.  In fact, printing from Acroread prints everything red, including transparent backgrounds.  Postscript problem?

---

### Post by nikkkko on 2007-10-31
fcoster

did you get this to work?  I have been able to print from Evince, but only occasionally and I don't know why.  Printing from Acroread turns everything red and I can't fix that either.

---

### Post by fcoster on 2007-10-31
nikkko

Thanks for the tip. Acroread indeed prints and seemingly without issue (its just an old black & white laserjet--so no color issues to worry about here). Evince is still not printing for me; but I've printed a couple PDFs with Acroread without problems. Thanks for the heads up on this one. (tubasoldier I haven't tried KPDF, though I may soon too).

(Other than this one weird little fluke with Evince, gutsy has been great for me. Having all the compiz-fusion effects makes me want a little more RAM--I've only got half a gig right now; and everything else is working flawlessly.)

Thanks again!

-fcoster

---

### Post by nikkkko on 2007-11-01
Apparently there is a bug with Evince whereby it won't [print out pdf's greater than a certain size]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/44989"), so if your pdf's were big, that's possibly the reason. Anyway, glad Acroread works for you.

Now if anyone out there knows why my hp color laserjet 2605 prints red with Gutsy, I'd be much obliged.

---

### Post by rrwo on 2007-11-11
I can print PDFs with Acrobat with no problems that I can see.  But for various reasons I need to print with Evince, and it doesn't work since I've upgraded to Gutsy.

What happens is that it sends blank pages to the printer. (Sometimes a stray line from figures is printed, but that's it.)  Same thing when I look at the pages with print preview.

Nothing shows up in the CUPS error logs about it.

---

### Post by shakma on 2007-12-19
Just want to throw my hat in the ring...

I have no problem printing from Evince to the local HP Deskjet D2430... except that this printer is just slooooow!

However, when I send the print to the networked HP LaserJet 4100N... nothing comes out.  

I haven't tried Acroread or KPDF yet, but I'll give it a shot.  Is there a reason it could just be an HP LASERjet problem??

Peace.

---

### Post by nikkkko on 2007-12-20
> **shakma said:**
> 
However, when I send the print to the networked HP LaserJet 4100N... nothing comes out.  

I haven't tried Acroread or KPDF yet, but I'll give it a shot.  Is there a reason it could just be an HP LASERjet problem??

I have read of some incidences when the printer light blinks, the document queue shows the file being processed and then sent to the printer but the printer simply stops blinking and nothing is printed.  You can check on the hplip site for a solution if this is your problem.

---

### Post by julien-1993 on 2008-02-22
I have exactly the same problem,

Test print ok, printing in openoffice ok, 

when i try to print from evince, nothing happens, no light blinking, nothing....

gutsy server

---

### Post by nikkkko on 2008-02-22
> **julien-1993 said:**
> I have exactly the same problem,

Test print ok, printing in openoffice ok, 

when i try to print from evince, nothing happens, no light blinking, nothing....

gutsy server

Did you see my earlier post about evince?  There appear to be ongoing problems for pdf's over a certain size.  Try Acroread.  

However, if by chance you are printing to a HP Color Laserjet, Acroread will probably print some documents with a red wash.  That's an ongoing problem which will apparently be solved in the next release.

---


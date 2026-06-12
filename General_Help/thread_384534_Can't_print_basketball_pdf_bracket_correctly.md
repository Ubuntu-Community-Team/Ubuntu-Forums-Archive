---
title: "Can't print basketball pdf bracket correctly?"
date: 2007-03-14
forum: General Help
---

### Post by wargames on 2007-03-14
Ok, I tried printing this pdf NCAA basketball bracket out around ten times and every time the end gets cut off. Is this some kind of problem with evince PDF viewer? I can't seem to change the page layout in order to reduce the top margin.

Here's the basketball bracket:
[http://assets.espn.go.com/i/ncaa/07men_bracket.pdf](http://assets.espn.go.com/i/ncaa/07men_bracket.pdf)

My printer is a HP PSC 2355v all-in-one using the PSC 2350 driver. I've tried changing the paper from A4 to Letter, but still it will not print correctly.  It will put about a half inch top margin and  start printing but will cut the bottom 3% of the page off. I've never been able to get the whole thing to print on one page like it's suppose to. Is this a evince problem, printer driver issue, or what? I refused to boot into Windows just to print a single page PDF file.

Any help out there?

---

### Post by stchman on 2007-03-14
> **wargames said:**
> Ok, I tried printing this pdf NCAA basketball bracket out around ten times and every time the end gets cut off. Is this some kind of problem with evince PDF viewer? I can't seem to change the page layout in order to reduce the top margin.

Here's the basketball bracket:
[http://assets.espn.go.com/i/ncaa/07men_bracket.pdf](http://assets.espn.go.com/i/ncaa/07men_bracket.pdf)

My printer is a HP PSC 2355v all-in-one using the PSC 2350 driver. I've tried changing the paper from A4 to Letter, but still it will not print correctly.  It will put about a half inch top margin and  start printing but will cut the bottom 3% of the page off. I've never been able to get the whole thing to print on one page like it's suppose to. Is this a evince problem, printer driver issue, or what? I refused to boot into Windows just to print a single page PDF file.

Any help out there?

I had the exact same problem.  Apparently the default Ubunt .pdf reader is kind of lousy (evince).  I went to the Add/Remove and installed Acrobat Reader and it works GREAT.  The Acrobat reader when you select print will let you specify 8.5 x 11 (US Letter).  Evince wile free does suck a little bit.  I was able to print to my color page.  Also with evince the letters of pdfs are blurry, Acrobat reader they are nice and clear.

What kills me is that Acrobat for XP is a bloated pig and for linux it is a nice fast loading streamlined application that does not install toolbars as other crap.  Why can't more applications be that way for XP as I guess linux users don't tolerate BS being installed.

---

### Post by IcemanV9 on 2007-03-14
I can print ESPN bracket just fine (woot!), but not from ncaasports.com. Weird. Evince is okay (sometimes). I tried not to install Adobe (closed source) as much as I can.

Anyway, it varies on everyone's box and printer.

---

### Post by stchman on 2007-03-14
> **IcemanV9 said:**
> I can print ESPN bracket just fine (woot!), but not from ncaasports.com. Weird. Evince is okay (sometimes). I tried not to install Adobe (closed source) as much as I can.

Anyway, it varies on everyone's box and printer.

I am big on what works.  If Adobe works the best I will use it.  It did not ask me for money and I don't really care about altering the source code.  If there is a better .pdf viewer than Acrobat for Ubuntu I will use it.  I use Foxit on Windows as I thought it was the better .pdf viewer.  I tried several .pdf viewers on Ubuntu and found Acrobat to be the best.

---

### Post by wargames on 2007-03-15
Thanks for the suggestion on using Adobe Reader but I'm not going to install a huge 22MB application just to print a PDF file. 22MB seems awefully bloated to me. I'm on dial-up (no broadband available in my part of the U.S.) so 22MB would take hours to complete. I tried gpdf but it sucks just as much as evince and produces the exact same result in printing.

Maybe someday they'll fix this software to work properly. I'll just have to make do without the basketball brackets. :(

---

### Post by wargames on 2007-03-15
Well, I finally got it without using Adobe Reader. I found out that you can view PDF's with Gimp. So I then used Gimp to view it and set the anti-alaising to strong for both settings, then saved it to JPEG using 100% quality. Then opened OpenOffice and set the page to Landscape and inserted the JPEG version of the PDF. Centered the image and printed it out just fine. Not a pretty method but works and saved me from installing Adobe Reader. :)

---


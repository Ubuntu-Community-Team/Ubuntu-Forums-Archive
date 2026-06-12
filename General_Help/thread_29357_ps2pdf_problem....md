---
title: "ps2pdf problem..."
date: 2005-04-24
forum: General Help
---

### Post by BigRod on 2005-04-24
ps2pdf randomly stopped working on me today.  

I was able to convert 2 ps documents to pdf no problems, the third and fourth that I needed to convert get corrupted (and I suspect others won't either). The top parts of the documents get converted alright, but the rest is just junk.  I looked at the man pages for ps2pdf and they are no help.

All that I am doing is this:

ps2pdf doc1.ps doc1.pdf

Not much to mess up, but aparently something has gone wrong.  Is there a way to reinstall it?  I am going to try just apt-get'ing it, but I don't think that is going to help.

---

### Post by mendicant on 2005-04-24
Reinstalls can be done like:

aptitude reinstall gs-common

Of course, it's unclear if that will help your situation--you suspect that ps2pdf itself is corrupt?

---

### Post by BigRod on 2005-04-24
[QUOTE=mendicant]Reinstalls can be done like:

aptitude reinstall gs-common

Of course, it's unclear if that will help your situation--you suspect that ps2pdf itself is corrupt?[/QUOTE]

I am honestly not sure.  It just stopped working.

I didn't do anything other than what I normally do with it, so it is very strange.

---

### Post by mendicant on 2005-04-24
When you say the rest of the file is junk, what do you mean? PDF isn't human readable like PS, so it would normally appear to be junk--except for the end of the files, which seem to contain font information.  

I assume xpdf is failing on the document, though?  You might want to try out some simple .ps files.  I can send some very simple hand built ones if you want.

---

### Post by BigRod on 2005-04-24
By 'junk' I mean that the top portion of the generated pdf (in xpdf that is) looks just like the ps file (when viewed in whatever the ps viewer is called).  After about the top inch (relatively) of the page in the pdf nothing is readable, but the initial ps file looks completely normal all the way down the page.

If you want to send some, I'll give it a shot, but I'm skeptical as to what the results will be.

---

### Post by crazybill on 2005-04-24
How much RAM in your box and how large are the ps files that you are trying to convert?

---

### Post by BigRod on 2005-04-24
512 megs RAM, 512 swap

The files are only 300k or so.

I did realize one thing that maybe will help solve this.  The files I was able to convert yesterday were created BEFORE I upgraded to Hoary.  The ones I have had problems with are ones created AFTER I upgraded.  So, perhaps the real issue is something with the postscript printer driver in hoary.  

Does that conjur up any new ideas?

---

### Post by mendicant on 2005-04-24
You can try the attached.

---

### Post by mendicant on 2005-04-24
Incidentally, I tried ps2pdf on that file, and it works fine.

---

### Post by BigRod on 2005-04-24
Well, that file worked like a charm.

Now I'm really confused.

---

### Post by BigRod on 2005-04-24
Just to make sure, I tried it on one of my files (a print from Mozilla to PS) and again it didn't work.

---

### Post by mendicant on 2005-04-24
Well, the file I gave you was a hand built (educational) postscript file.  Have you tried new files printed from mozilla?  Have you tried other postscript files from other apps?

---

### Post by BigRod on 2005-04-24
No, I'll have to try some other apps.  Maybe something is jacked up in Mozilla.

---

### Post by BigRod on 2005-04-24
Okay, well I tried a file printed from OpenOffice and it worked fine too.  Must be something about Mozilla.

---

### Post by BigRod on 2005-04-24
Yep, definitely something wrong with the way mozilla prints to ps, but I'm not sure how it is happening or how to fix it.  

I attached a file to show exactly what is happening between .ps and .pdf.

I'm going to screw around with the print settings and see if something will fix it.

---

### Post by akaihola on 2007-05-23
I have an issue which may be related:

This makes my 512M RAM Feisty machine swap wildly and get very slow:
echo Test | mpage -b A4 -L 62 -1o - | ps2pdf -sPAPERSIZE=a4 - test.pdf

(apt-get mpage to get the mpage utility)

---


---
title: "how to paste image into Gimp"
date: 2006-07-10
forum: General Help
---

### Post by DaveRowell on 2006-07-10
Is there some way to paste an image from the system clipboard into The Gimp as a new image?  As far as I can see Gimp will do that only from the Gimp clipboard - am I missing something???

Specifically I am trying to copy part of a PDF file using Adobe Reader and creating a new image in Gimp to save with my family data.  I can do this without problems if I use Paint Shop Pro under Wine rather than Gimp but it really shouldn't be necessary.

---

### Post by Polygon on 2006-07-10
i just tried this and it doesnt seem to work for me either, i thought that going to file>aquire>paste as new   would do it , but it doesnt seem to work.

would be a nice feature to suggest to the developers though

---

### Post by Paerez on 2006-07-10
You should be able to say File -> New (the dimensions should be filled in from the clipboard). Then once you have a new image, right click inside the image, and say edit -> paste into.

good luck

---

### Post by DaveRowell on 2006-07-11
Nope!  That didn't work either.  BTW the image size in NEW was apparently way off base - nearly square when the clipboard image was a newspaper column.

---

### Post by Paerez on 2006-07-11
from my experimentation it looks like Adobe's PDF viewer copies stuff into KDE's clipboard, because I could paste into KDE apps but not gnome ones. I don't have Evince on this comp, but can you copy images using Evince? Maybe then it will go to Gimp.

---

### Post by coolclassic on 2006-07-11
Worked for me. Right click on image-view in embedded image viewer-right click-copy image

Open gimp select new and paste.

---

### Post by DaveRowell on 2006-07-13
I just don't understand :confused: your post, Coolclassic.

Would you please explain more fully?

Thanks

---

### Post by coolclassic on 2006-07-13
Sorry! I read it again and i see what you mean.

I use konqueror so I don't know if that will make a difference.

In konqueror I am able to display any image. I would also be able to view the image within konqueror using the embedded image viewer which is built into konqueror, this will allow me to copy the image and paste it into gimp or other software.

---

### Post by trollzor on 2006-07-13
C&P any image and then open a new file in the gimp and it should have the dimensions of the clipboard image. This works for png, jpg, gif etc.

PDFs on the other hand, the way I deal with them is to start the gimp then just simply drag and drop the PDF onto the main gimp toolbar. This then gives you a load postscript import dialogue as attched, plug in your prefs and the page number and you have that page from the PDF as an image in the gimp. If you need less than the whole page, just cut and paste that image once it's there.

You weren't too clear about what you were trying to do but I hope this helps.

cheers,

trollzor

---

### Post by DaveRowell on 2006-07-17
What I am trying to do:
I have a PDF of an entire newspaper page (LOTS of them).  On the page is an obituary (typically 1 column wide by 3 or 4 inches long) that I want to copy and keep with the person's genealogy information.  Using Acrobat Reader I can 'take a snapshot' of the obituary to the system clipboard.  I want to paste into Gimp so that I can add text showing the source information and perhaps enhance the image a bit.  But Gimp seems to ignore the system's clipboard.](*,) 

I'm running Ubuntu not Kbuntu.

Since I can't figure out how to paste the system clipboard into Gimp I have to run Paint Shop Pro on Wine - paste into PSP - save as TIF - import the TIF into Gimp.  I'd do it all in PSP except that it can't figure out the keyboard under Ubuntu - PSP crashes if I press most letter keys - 'A' and numerals work.

---

### Post by coolclassic on 2006-07-17
I had a look in synaptic and found this package that convets pdf to html it may be useful to you.

pdftohtml

---

### Post by stu on 2006-07-17
I have a feeling Adobe doesn't play well with the GNOME clipboard =/

Well, obviously this is another workaround, but if you use the 'Open' dialog to open the PDF file with GIMP, it will allow you to import whichever pages you like, and render them at a size of your choosing. Then you can touch up and save to TIF.

---

### Post by DaveRowell on 2006-07-17
I feel like a complete ***! :-#  I hadn't realized that Gimp could open a PDF.

I just tried opening a page in Gimp - copying an obit. - pasting it as a new file - adding text - it all works :p

---


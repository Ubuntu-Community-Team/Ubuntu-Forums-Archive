---
title: "dolphin file browser, with pdf preview and info"
date: 2014-11-05
forum: General Help
---

### Post by sparky-steve on 2014-11-05
Hiya!

I'm running kubuntu 14.04, using the default dolphin file browser, and have installed & set up previews for .pdf files.

However, underneath the .pdf preview is file information (Type, Size, Tags etc) - but all that is doing for me is reducing the space available for the preview; 

In my work, I need to rename several hundred pdf files every few days, and even worse, I just lost my 24" widescreen monitor, meaning I'm working on a laptop; So I need to maximize the space available for the preview.....

I've looked around the options, even unlocked the panel, but it appears that this information pane is mandatory with the document preview.

Can anyone else comment or advise?

Thanks!

SS

---

### Post by sparky-steve on 2014-11-05
BTW, I am open to alternative file browsers; My requirement is simple: a vertical pane for viewing a directory & another vertical pane with the preview, as big as is possible.

---

### Post by SeijiSensei on 2014-11-06
I  have to ask this:  Are you manually renaming hundreds of files each day?  Is there no pattern to the renamings that could be automated with a bash script?  This seems like an enormous waste of your time.  Do you have to display each file to determine its integrity before renaming?

---

### Post by ringstaart on 2014-11-06
> **SeijiSensei said:**
> I  have to ask this:  Are you manually renaming hundreds of files each day?  Is there no pattern to the renamings that could be automated with a bash script?  This seems like an enormous waste of your time.  Do you have to display each file to determine its integrity before renaming?
If the renaming is based on the text in the pdf files, lesspipe is a simple tool that will try to output the contents of the pdf file as plain text. If the title is right at the start of the document, it becomes really easy to automate.

---

### Post by sparky-steve on 2014-11-06
Hi,

The scans are manually scanned in a shop, and stored on googledrive, I then grab them and yes, I have to manually look at the files - not for integrity - but for the filename, which is based on the vendors name, the invoice date and the invoice number.

I have tried gocr, pdftotext, ocrfeeder and tesseract to try OCR, but the image quality is not good enough to give proper output to automatically rename these files; Some vendors send their invoices direct from their system via pdf email, and these are easy to convert with a batch script; Slowly more & more are moving to that, but until that day, I have to manually do it! (Wow! That was a long explanation LOL)

So yes, I have to display the file; even worse, on dolphin, because of the "extra" info displayed below the preview, the image is sometimes not big enough to read the text; In which case I have to hit enter to open the file, write down the details, close and rename (F2).

I have made it slightly bigger by allowing windows to cover the bottom pane, and this is certainly an improvement, but if I can get rid of the additional info under the preview image I think it will make a big difference.

I've also tried krusader and and thunar, all to no avail.

SS

---

### Post by ringstaart on 2014-11-06
> **sparky-steve said:**
> Hi,

The scans are manually scanned in a shop, and stored on googledrive, I then grab them and yes, I have to manually look at the files - not for integrity - but for the filename, which is based on the vendors name, the invoice date and the invoice number.

I have tried gocr, pdftotext, ocrfeeder and tesseract to try OCR, but the image quality is not good enough to give proper output to automatically rename these files; Some vendors send their invoices direct from their system via pdf email, and these are easy to convert with a batch script; Slowly more & more are moving to that, but until that day, I have to manually do it! (Wow! That was a long explanation LOL)

So yes, I have to display the file; even worse, on dolphin, because of the "extra" info displayed below the preview, the image is sometimes not big enough to read the text; In which case I have to hit enter to open the file, write down the details, close and rename (F2).

I have made it slightly bigger by allowing windows to cover the bottom pane, and this is certainly an improvement, but if I can get rid of the additional info under the preview image I think it will make a big difference.

I've also tried krusader and and thunar, all to no avail.

SS
You could try a simple script that shows you a pdf file, lets you rename it after you close the viewer, and repeats this for all documents.

mupdf is a good viewer for this. It's really lightweight, and doesn't have a real user interface - it just shows you the document, and you control it with keybindings. You wouldn't have to take your hands off the keyboard.

---

### Post by sparky-steve on 2014-11-06
> **ringstaart said:**
> You could try a simple script that shows you a pdf file, lets you rename it after you close the viewer, and repeats this for all documents.

mupdf is a good viewer for this. It's really lightweight, and doesn't have a real user interface - it just shows you the document, and you control it with keybindings. You wouldn't have to take your hands off the keyboard.

That's an interesting idea... I'll certainly look into that....

Thanks!

---

### Post by sparky-steve on 2014-11-06
> **ringstaart said:**
> If the renaming is based on the text in the pdf files, lesspipe is a simple tool that will try to output the contents of the pdf file as plain text. If the title is right at the start of the document, it becomes really easy to automate.

I'm short on time today, but just ran this quickly, and the output was nothing; It could be that I've not really read the manpage.

```

steve@X501A:/media/steve/DATA/Work$ lesspipe Scan0130.pdf 




steve@X501A:/media/steve/DATA/Work$ 

```

---

### Post by ringstaart on 2014-11-06
> **sparky-steve said:**
> I'm short on time today, but just ran this quickly, and the output was nothing; It could be that I've not really read the manpage.

```

steve@X501A:/media/steve/DATA/Work$ lesspipe Scan0130.pdf 




steve@X501A:/media/steve/DATA/Work$ 

```
That's because it's a scanned document - it's just a glorified collection of image files. With computer-generated pdf files, the text is typically encoded in the pdf file itself, so programs can read the text easily.

---

### Post by sparky-steve on 2014-11-06
Exactly what I thought - though gocr did have *some* luck, but it was consistently inconsistent....

SS

---


---
title: "OCR with ocrfeeder and tesseract (or tesseract-ocr)"
date: 2013-06-29
forum: General Help
---

### Post by pwabrahams on 2013-06-29
I'm running Kubuntu 13.04 (raring) on a Lenovo laptop.  I have a scan of a page of typed text, in both pdf and tiff formats.  I'm trying to use OCR (optical character recognition) to turn the image of that scan into the actual text.

From what I read, the best tool for this is **ocrfeeder**, together with **tesseract**.  It appears that the correct procedure is to go into **ocrfeeder**, then select File / Import PDF.
Doing that, I get a screen that displays the scanned image, though for some reason the file listing to the left shows it as a jpg, not a pdf.  I now go to Document/Recognize Document.  What shows up as the text, when the recognition is done, is just a single capital A.  It appears that tesseract is being used for the recognition.

What's particularly frustrating is that when I first started fiddling with this, I actually did get the text of the document to display, but I didn't know how to save it at that point.  Now I can't get the text to display at all.   The documentation on **ocrfeeder **  is very sketchy.   To confuse matters further, the actual OCR program seems to be named "tesseract-ocr", not "tesseract".  I've also seen recommendations for using gscan2pdf, but when I tried that I found that it was looking for "tesseract" rather than "tesseract-ocr".

I'd appreciate any advice or pointers to better explanations.

---

### Post by pqwoerituytrueiwoq on 2013-06-29
tesseract requires the file be in tiff format but be spelled as ".tif"
i suggest scanning at at least 200DPI for a accurate conversion to text
There is some software in my signature that can give you a front end for scanning via scanimage and tesseract

This is how is suggest using tesseract
1st convert the image to the format it likes
[FONT=courier new]convert /path/to/MY_IMG.png -fx '(r+g+b)/3' /tmp/out.tif[/FONT]
now we can get a text file (languate is et to english)
[FONT=courier new]tesseract /tmp/out.tif newtxtfile -l eng[/FONT]
now lets read that text file
[FONT=courier new]cat newtxtfile.txt[/FONT]

this has a list for what letters mean what language (uptodate as of ubuntu 13.04)
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/inc/langs.json](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/inc/langs.json)

The package name is [FONT=Courier New]tesseract-ocr[/FONT] the executable file is [FONT=Courier New]/usr/bin/**tesseract**[/FONT]

---

### Post by pwabrahams on 2013-06-30
I took your suggestion and used tesseract directly without getting ocrfeeder involved.  That worked - thanks.  It made very few errors.

It probably would have been easier to do the job via ocrfeeder, except that there's no detailed documentation on ocrfeeder that I can find, and many of the features and options are very mysterious (to me at least).

---

### Post by claracc on 2013-06-30
Have you read: [https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR) ?

It can give you more information about the subject.

---

### Post by pwabrahams on 2013-06-30
The community write-up you cited mentions ocrfeeder and describes it in general terms but provides no details on how to use it.

---

### Post by claracc on 2013-06-30
Yes, but I refers to the information :

```
OCRFeeder

OCRFeeder can do this too. Sadly it doesn't seem to work very well yet. 
```

Which can explain you why the program doesn't work as well as required to do the task.

---

### Post by pqwoerituytrueiwoq on 2013-06-30
> **pqwoerituytrueiwoq said:**
> There is some software in my signature that can give you a front end for scanning via scanimage and tesseract[FONT=Courier New][/FONT]Updated link in signature to link to the change log, where there are new versions

---

### Post by pmasson on 2013-08-09
> **pqwoerituytrueiwoq said:**
> i suggest scanning at at least 200DPI for a accurate conversion to text

This is how is suggest using tesseract
1st convert the image to the format it likes
[FONT=courier new]convert /path/to/MY_IMG.png -fx '(r+g+b)/3' /tmp/out.tif[/FONT]
now we can get a text file (languate is et to english)
[FONT=courier new]tesseract /tmp/out.tif newtxtfile -l eng[/FONT]
now lets read that text file
[FONT=courier new]cat newtxtfile.txt[/FONT]

The package name is [FONT=Courier New]tesseract-ocr[/FONT] the executable file is [FONT=Courier New]/usr/bin/**tesseract**[/FONT]

I used the above approach after installing OCRFeeder and trying several times to extract the text from a PDF. After downloading OCRFeeder from the Ubuntu Software Center, and selecting "Import PDF" the application crashed each time after running "Recognize Document." Tesseract worked perfectly. While I did not have a sophisticated layout, i.e. columns, tables, headers, etc. Tesseract, and acknowledging the utility will only provide the characters--no formatting, e.g. bold, underline, italic, font size, etc.--it was simple and quick.

A tip for others trying to extract the text from a multi-page PDF would be to open the PDF in GIMP using the "Open As Layers." This will pull each page as an image and you can then save a copy of each page as a .tif.

Thank you **pqwoerituytrueiwoq**

---


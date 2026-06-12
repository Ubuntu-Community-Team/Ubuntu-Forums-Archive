---
title: "Tesseract documentation and what I did"
date: 2013-11-21
forum: General Help
---

### Post by imconfused2 on 2013-11-21
Xubuntu 12.04. Tesseract installed with Synaptic Package manager.
[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR) gives instructions for tesseract.  I followed them on a png document I downloaded and the results were unreadable.  According to the above website instructions the graphics has to be converted to tif with gimp along with some other parameters.  Spent a long time playing with the gimp and still no readable result.

Tesseract is supposed to be accurate so I started searching.  It can't read small letters.  Instead of using Gimp I used the command line working in the directory I had the file located:

**convert -resize 400% document.png documenta.png **

         (note:This gave me a much bigger file.  On info convert the resize is mentioned but is not really documented in the list of options.  I picked it up in searching the web and it is on the documentation of the developers website [http://www.imagemagick.org/script/command-line-options.php#resize](http://www.imagemagick.org/script/command-line-options.php#resize) .)

Then I used tesseract on the documenta.png with the following command:

**tesseract documenta.png  document**

The output in the directory was document.txt  The .txt extension was added automatically.

The document was excellent with some editing needed but the output went from garbage to almost gold by just enlarging the documents.  Tesseract is an excellent graphics to text converter that will work with png documents.   It needs reading glasses to do the job however.

---


---
title: "PDF Looks/prints great on Windows, but is wrong on Ubuntu"
date: 2020-05-23
forum: General Help
---

### Post by martin-colello on 2020-05-23
So, I created a pdf label file on [avery.com]("https://avery.com").  On Windows 10 with Acrobat Reader an individual label looks like this:

[IMG]https://i.ibb.co/RY1tgXk/2020-05-23-11-19-25-15264-kitten-purina-pdf-Adobe-Acrobat-Reader-DC.png[/IMG]

When I open the same file on Ubuntu Mate 20.04, it looks like this, and prints outside the label.  (Note the ugly yellow.)

[URL="https://preview.redd.it/oy8skja64k051.png?width=488&format=png&auto=webp&a7835095"][IMG]https://i.ibb.co/YypMDtC/2020-05-23-11-20-46-Home-Monica-Lenovo.png[/IMG]

[/URL]I have tried the following pdf  readers so far:  Evince, Okular, Atril and LibreOffice Draw and Writer.   They all look the same, ugly yellow and text not fitting on label.
Anyone have any ideas?  Thanks so much in advance!

[URL="https://preview.redd.it/oy8skja64k051.png?width=488&format=png&auto=webp&a7835095"]
[/URL]

---

### Post by SeijiSensei on 2020-05-23
What about GIMP? It will import PDFs.  

As for the background, I wonder if it might be a mismatch between the RGB and CMYK color models. I bet Avery uses the latter. If this is the issue, you might find this article helpful: [https://wiki.archlinux.org/index.php/GIMP/CMYK_support](https://wiki.archlinux.org/index.php/GIMP/CMYK_support)

Sanrio's getting pretty [loose about licensing]("https://twitter.com/WeRHelloKitty/status/1263146811084201984") Hello Kitty these days it seems.

---

### Post by dragonfly41 on 2020-05-23
Explore using Scribus in Ubuntu repo.  It deals with professional print quality CYMK.
And with Inkscape creating your vector objects you can design your own label(s) in desktop.

---

### Post by martin-colello on 2020-05-23
OK, just got done trying GIMP and Scribus, they both look the same as all the others.  I don't understand how this is even possible, isn't a PDF a standard designed to be the same on any platform?

---

### Post by cbraxton on 2020-05-23
You might give Foxit PDF reader a try. There is a native Linux version or you can run the Windows version under wine.

[https://www.foxitsoftware.com/pdf-reader/](https://www.foxitsoftware.com/pdf-reader/)

Another possibility might be to open the PDF in Chromium or Firefox. 

Adobe Reader was available for Linux through version 9 and although no longer supported it can still be found. I have it running on my Ubuntu 16.04 desktop, but it needs some 32-bit libraries which might not be available in 20.04:

[https://www.fosslinux.com/1776/how-to-install-adobe-acrobat-reader-in-ubuntu-and-linux-mint.htm](https://www.fosslinux.com/1776/how-to-install-adobe-acrobat-reader-in-ubuntu-and-linux-mint.htm)

---

### Post by DuckHook on 2020-05-23
Many software developers and OEM manufacturers do not follow published standards. They test their apps/devices to make sure that they work with Windows' wonky implementation—in fact, will even depart from those standards on purpose to accommodate Windows' bugs—and the rest of the computing world are not given another passing thought. It is possible that Linux apps are showing the strange colour precisely because they adhere to published standards whereas the Avery software is using quirky output designed to work around Windows' flaws.

I'm not claiming that this is definitely the case here, but it's a known dynamic in the computing world and has existed for as long as Windows has dominated the desktop.

Or it could be as simple as SeijiSensei's alert to check your colour model. Have you checked your colour model?

---

### Post by Dennis N on 2020-05-23
Please supply a link to the actual PDF file.

---

### Post by HermanAB on 2020-05-24
Howdy,

You could install Adobe Reader on Linux and if you want a working file 'Print' it to a new file.

---

### Post by martin-colello on 2020-05-24
> **Dennis N said:**
> Please supply a link to the actual PDF file.

Here is a link to the actual file.  I'm very interested to know why it doesn't work properly on Ubuntu.

[https://gofile.io/d/lL0Ash](https://gofile.io/d/lL0Ash)

---

### Post by webaake on 2020-05-24
Did you check the printer settings in Linux? Paper formats differ between countries (US / Europe). And then fonts/typefaces. What fonts did the designer use? Are they included in the PDF? Do you have them installed? And same font/typeface can differ betwwen Win and Linux in kernig, size and more.

---

### Post by Dennis N on 2020-05-24
If you don't want the yellow, you could open the PDF in Gimp and change any yellow to white. Then export back to png or pdf. Would that be an acceptable fix? My result attached as proof:

(The exported PDF viewed in qpdfview shows no yellow.)

---

### Post by rbmorse on 2020-05-24
FWIW, I downloaded the file, opened it with MasterPDF Editor v 5. and printed it on my HP CP2025DN colored laser printer.  The image is correct in both Master PDF Editor and on the printed page.  

However, I see the yellow cast on the image when opened in Document Viewer or LibreOffice Draw. Maybe something in Gnome?

---

### Post by daniewicz on 2020-05-24
I am running Ubuntu 20.04. I installed the Adobe Reader 9.5.5-1 deb file and the pdf displays as it should without the yellow background.

---

### Post by Morbius1 on 2020-05-24
> **cbraxton said:**
> You might give Foxit PDF reader a try. There is a native Linux version or you can run the Windows version under wine.

[https://www.foxitsoftware.com/pdf-reader/](https://www.foxitsoftware.com/pdf-reader/)


And this is the way it renders in Foxit - the Linux version:
[ATTACH=CONFIG]286001[/ATTACH]

---

### Post by Holger_Gehrke on 2020-05-24
Another reader that does it without the yellow background is the built-in JavaScript pdf-viewer in Firefox (although it gives a warning that it might not be displaying it correctly). Since most of the viewers on Linux use the Poppler library for doing the actual rendering, this just might be a bug in that library. The viewers (Foxit, Firefox, Master PDF and the really, really old Acrobat that nobody should be using) that display it right don't use that library ...

Holger

---

### Post by monkeybrain20122 on 2020-05-24
I think that is because all free Linux pdf readers use poppler as the backend so if there is a glitch with formatting or if different standards are used the problems will be shared by all. Instead of installing the unmaintained bloatware that is adobe a simple way is to use PDFXchange viewer in wine.  It is light, runs  perfectly in wine and always works for these oddly formatted pdfs when the usual Linux solutions fail.  I just tried it with your image, there is no yellow background (attached)

P.S. There is also no yellow background after printing out from PDFXchange (with cups-pdf) and then open in qpdfview.

P.P.S Foxit PDF reader for Linux works too.

---

### Post by Impavidus on 2020-05-25
gv, not based on poppler, but on ghostscript, displays it without the yellow too.

---

### Post by ullanus on 2021-02-11
I would like to know why did you create a pdf label file on avery.com in the first place? I looked at the photos, and I didn't see any yellow. In fact, I didn't see any difference between the two photos. I have never tried to open pdf files on ubuntu, so I must admit that I have no idea why this is happening. To me, it is obvious that if you've tried different pdf readers and nothing changed, the problem must be in the differences between the Windows operating system and the Ubuntu operating system. You can also try to [[COLOR=#000000]use a pdf converting tool[/COLOR]]("https://pdf-ocr.com") that works both on Windows and Ubuntu operating systems. Good luck!

---


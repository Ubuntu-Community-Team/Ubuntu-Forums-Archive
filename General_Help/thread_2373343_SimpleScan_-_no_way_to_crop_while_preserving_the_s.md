---
title: "SimpleScan - no way to crop while preserving the side ratio?"
date: 2017-10-05
forum: General Help
---

### Post by 1002285 on 2017-10-05
I use SimpleScanner for my scanning needs and it is perfect for me in every aspect but one. I am not able to crop a scanned page so that the cropped part maintains the A4 side ratio. I can set the page to remain A4, but only in its original size. But I really often need to change the size so that I do not waste space on useless white margins and get a better result for viewing on my tablet computer, for example. Also, it is critical if I want to get a beautiful printout of the scanned page.

I like the quality and simplicity, not having to think too much about points of graphics that I do not understand.

I know that there are other scanner applications but they all seem to be much more difficult and time consuming.

Can SimpleScanner be used in the way that I need; or can I send this request somewhere where it might be taken into account in the future?

---

### Post by Bucky Ball on 2017-10-05
Crop the scan how you like. Scan and save. Open a Libreoffice document or a Draw document. Insert the graphic (your scan) into the document. Resize the image to fill the A4 page. Done.

You can't really expect your cropped section to suddenly blow up in the scan preview to fill the A4 size. You are scanning an A4 page and the preview is giving you an exact replica of what you're scanning. A 'real world' image. You do the resizing *after* the scanning.

Good luck.

---

### Post by HermanAB on 2017-10-05
You could make a little imagemagick script to do what you want.

---

### Post by ajgreeny on 2017-10-05
Your problem is really explained by the name of the application you are using, ie, **Simple**Scan, and it means what it says, it's simple both to use and in its limited flexibility.

There are changes you can make to various scan elements from the Document ->Preferences menu, which I assume you must have found, but for the things you are wanting, ie limiting the area actually scanned from a page and perhaps changing the dpi or colour output on the fly, it sounds as if you might do better with xsane, though you will still find that you need to resize the output image in order to use it in whatever way you want, as most (all) scanning programs that I have ever used create an image but do not do any more with it than create it.

---

### Post by gordintoronto on 2017-10-05
When I scan something, I assume I will process the image with GIMP, unless the defaults produce just what I wanted.

---


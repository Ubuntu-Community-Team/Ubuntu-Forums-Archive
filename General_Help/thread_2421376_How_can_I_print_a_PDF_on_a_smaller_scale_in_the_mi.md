---
title: "How can I print a PDF on a smaller scale in the middle of the page?"
date: 2019-06-20
forum: General Help
---

### Post by janlz on 2019-06-20
Hello,
I'm trying to print a document in a different scale using my printer. The problem is that when I print it on a smaller scale, the text is printed in the upper-left corner, which makes it difficult to print both sides of the document because the pages would be at different corners.

I attached an example document on a 50% scale so you can see what I'm talking about: [ATTACH]283461[/ATTACH]

Is it possible to print the document centered horizontally and/or vertically so both pages are on the same position? My printer is an HP LaserJet 1018 and I'm using hplip 3.17.10+repack0-5 (the version found in the Ubuntu repositories).

Thanks in advance.

---

### Post by him610 on 2019-06-20
This may not be exactly what you are looking for, but it is the only thing I could come up with. Do the following from the PDF viewer program (mine is Atril) -
Ctrl-P to bring up the Print configuration window, click on Page Setup, adjust Pages per side = 2
Click on Preview at the bottom of the window to see what It will look like before you print it.

On second thought, you could try this using LibreOffice Writer.
On a blank LibreOffice page, set the left and right margins to size.
Copy the text from your PDF document then paste into the LibreOffice page with the resized margins; adjust the fonts to size.
You may have to tweak each line ending manually. 
Save the file then export it as a pdf file.

I just tried this - it can be done.
good luck,

---

### Post by HermanAB on 2019-06-21
You should be able to change the PDF margins from the command line using a program called convert, which is part of imagemagick.  Read the man page.

---


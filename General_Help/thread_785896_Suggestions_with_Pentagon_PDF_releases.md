---
title: "Suggestions with Pentagon PDF releases"
date: 2008-05-07
forum: General Help
---

### Post by ricardisimo on 2008-05-07
As described [here]("http://www.counterpunch.org/stauber05072008.html"), the Pentagon got caught breaking the law [gasp!], and were obliged under the Freedom of Information Act to release [documents relating to their propaganda campaign]("http://www.dod.mil/pubs/foi/milanalysts/"). Unfortunately, they all appear to be poor-quality scans compiled as PDFs. Can anyone recommend a decent way to turn these into some variety of plain or rich text, so as to allow searches, formating, etc.? Perhaps some variety of OCR? Many thanks in advance.

---

### Post by ricardisimo on 2008-05-08
I think I've had some progress, but I'm not sure yet. I've installed both pdftk and ocrad from the repositories, and already had imagemagick, and so...
```
cd /home/me/Pentagon
```
puts me in the proper directory;
```
pdftk 19 Oct 06 Release Doc 2.pdf burst
```
gives me, in this example, 158 individual pdf pages from the original file, which had - evidently - 158 pages to it;
```
mogrify -format pgm *.pdf
```
converts all 158 pdfs to pgm files (I moved them and the terminal to a separate folder, by the way, so as not to modify the original pdf in any way).
The reason for all of this is to get ocrad to read an acceptable file, and pgm supposedly qualifies... but not so far. Is there perhaps a better OCR application out there for me to use here? Thanks.

---

### Post by ricardisimo on 2008-05-09
Well, I've finally gotten some workable results via tesseract 1.03 (in the repositories, and aid from this thread: [http://ubuntuforums.org/showthread.php?t=404619](http://ubuntuforums.org/showthread.php?t=404619). The ocube shell script towards the end is particularly useful, by the way, and if you open a folder stuffed with one-page .tiffs it churns out one, single, solitary, great big text file as its output, which was perfect for my purposes.

I'm curious if anyone else has tried the 2.03 version of tesseract from Google Code, if it is a marked improvement over 1.03, and if so, could you tell me how to compile it and install. I'm not real good with anything that isn't copying and pasting, unfortunately. Thanks.

---


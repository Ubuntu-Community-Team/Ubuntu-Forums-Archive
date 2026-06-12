---
title: "OpenOffice 2.2 cross platform formatting"
date: 2007-04-29
forum: General Help
---

### Post by homersbrain on 2007-04-29
I dual boot Ubuntu and Windows. I have some documents written in OpenOffice 2.2 under Windows and all saved as odt files, and also as doc files for backup. Both the odt and doc files look identical under windows with the same formatting and same number of pages (say 100) - great.

Then I boot up Ubuntu and load the same document in OO2.2 from the odt file. The number of pages is now far more than under windows (say 130). However if I load the doc file instead, then the formatting is exactly as it was under OO in windows (100).

It gets even more weird... I open the odt file again in ubuntu and then re-save it as a doc. Opening that new doc in OO (ubuntu) shows me 100 pages again!

What is going on? Why won't openoffice format the document properly under Ubuntu?

Has anyone else encountered these problems?

---

### Post by ajgreeny on 2007-04-29
Are you using the same fonts in windows and ubuntu?  Often they are slightly different, even if apparently the same in the two OSs, and this may cause different formatting of documents.  OOffice may just be using alternative fonts if they are not all the same files on both systems, so if necessary, install you needed windows fonts in ubuntu.  Also check your default page layout, margins, etc.

---

### Post by strabes on 2007-04-29
I've had problems like this even with msttcorefonts installed. I save an .odt on my ubuntu computer and open it on my university's windows computer and it's different lengths on each. Probably a font problem but I don't worry too much about it.

---

### Post by homersbrain on 2007-04-30
The fonts could not explain the problem. Remember, when saving the odt file as a doc, and then opening it again, it shows the correct formatting. When using OO at work for creating large reports - its important that the formatting is correct right down to the last character - a formatting difference of over 30 pages per 100 is utterly unacceptable. 

Also, I've found that exporting to a pdf yields the original 100 page length too. What you see is nowhere near what you get!

I am coming to the conclusion that there is a very serious critical bug in the linux/ubuntu OO package.

---

### Post by ajgreeny on 2007-04-30
I hear your point about the msstcorefonts, but I have actually copied my windows fonts into ubuntu and then installed them.  I will check next time I boot into windows if the formatting of odt and doc files changes between OSs.  I agree a 30% difference in page numbers is not acceptable, but at the moment can't help any further.

---

### Post by homersbrain on 2007-05-01
I think a bug report need filing about this - if OpenOffice on Ubuntu is seriously going to rival msoffice, then this really needs fixing!

How do I submit a bug report?

---

### Post by homersbrain on 2007-05-03
How do I submit a bug report for Oopenoffice 2.2?

---

### Post by mikewhatever on 2007-05-03
I think you should be looking in this direction [http://www.openoffice.org/](http://www.openoffice.org/)

---

### Post by niekko on 2007-05-06
Same problem here with OOo 2.2 .odt files between Ubuntu 7.04 and Windows XP Pro. The document is 99 pages under Windows and 94 pages under Ubuntu.

---

### Post by homersbrain on 2007-10-03
Has anyone tried whether OO2.3 has cleared up this problem for Gutsy?

---

### Post by homersbrain on 2007-10-22
bump! Anyone know if 2.3 fixes this?

---

### Post by omunozsj on 2007-11-06
I'm using OpenOffice.org 2.3 on several Windows pc's and I've just installed Ubuntu 7.10 onto my lap. In my organization we produce a lot of documents that need formating to be published.

My odt files DOESN'T look the same on Windows and Ubuntu.

I don't know if it's a Ubuntu problem or an OpenOffice problem.

---


---
title: "Exporting PDF from OpenOffice"
date: 2006-11-30
forum: General Help
---

### Post by DWright on 2006-11-30
I have found that when I use the "export to PDF" function in openoffice.org, the spacing of the characters is wrong.
For example: In the table of contents, the dots that go between the the chapter and the page number *should* be evenly spaced, thus:

Tile . . . . . . . . . . . . . 10

But in the PDF file they are sometimes bunched up like this
(pardon my ascii art)

Title . . .... . . .   .... .. 10

(It is not just the dots, some of the letters and numbers bunch up at random places on the pages) 
The document looks fine on screen in Openoffice, and in print preview, but not in the exported PDF file.
If I take the same file and load into Openoffice on Windows and on SuSE (10.1) the exported PDF is fine ... it is just wrong under Ubuntu (6.10).


Any suggestions?
:confused:

---

### Post by whizbaby on 2006-11-30
What happens when you open it with acroread? Still messed up?

---

### Post by DWright on 2006-11-30
The PDF file looks (and prints) the same no matter what you use to view it: Adobe Acrobat, xpdf, etc.
It just seems to be that the ubuntu flavor of openoffice renders a  different PDF file to the Windows and SuSE ones.

---

### Post by DWright on 2006-11-30
mmmm? not a lot of responses.
Thinking out loud:
I wondering if it is something peculiar about the fonts I am use?
...tied a variety of fonts ... same result.

I wonder if is something particular to my setup, eg a "bug" in my locale data .... maybe some sort of paper size mismatch?
I can't help but notice that edgy's openoffice tells me that A4 is 209.999mm x 296.999mm (instead of 210x297mm.
...played with some settings on this .... doesn't seem to have made and difference.

What else can I try?

---

### Post by DWright on 2006-12-01
Workaround: (pretty obvious really) I have installed CUPS pdf, and when I use that, my Openoffice documents convert to PDF perfectly.

---


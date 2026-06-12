---
title: "Force 90 degrees rotation when printing, center but not scale?"
date: 2015-01-01
forum: General Help
---

### Post by Lady Owl on 2015-01-01
I'm having an issue with printing. It is due to hardware really, but as I can't fix the printer, I seek a software solution, if there is one to be found...

 
I have a pdf that is arranged as portrait. When printing on both sides, however, it must be turned by the short, not long side, so the end result is rather landscape, really. Pages size A4, but they will be cut to a smaller size after printing, and the sides should match.

My printer doesn't have duplex printing, so I do it manually. In theory it should go fine, I know how to handle the pages. If the pages were turned by the long side (i.e. portrait) I would have the sides match, I could cut it just fine. BUT. The printer prints a page 7mm off (it seems to have issues with taking paper in correctly), and in my situation it makes the sides 14mm off compared to each other, as the sides are printed starting on opposite ends of paper. Too much when making planner pages. 

Now, the pages have wide margins, and the important part would actually fit on the paper even with 90 degrees angle. In that case it would not matter that it prints 7mm off - both sides would be moved in the same direction. But can it be done, and if, then how? There's no forced rotation option... Also I would then need centering, but absolutely not scaling the pages. 

I should get this sorted sooner than I can switch to a newer printer... any ideas?

(Feeding the paper on landscape would of course be an easy solution, but it is not possible for this printer.)

---

### Post by coldraven on 2015-01-01
Try using Libre Office Draw to compose the layout, it should be easy.

---

### Post by tgalati4 on 2015-01-01
*Inkscape* and *scribus*  can also be used to layout the page with the correct offsets.  Cheap printers will never give you perfect registration.  So you can either redesign your pages so that they can accept some sloppy registration, or get a printer with a proper duplexer and one that gets good reviews for page registration.  There are numerous PDF utilities that you can also use to manipulate the margins, rotation, etc:

```
apt-cache search pdf
```

---

### Post by schragge on 2015-01-02
```
axi-cache search pdf
``` is even better than *apt-cache*: it sorts results by relevance. But even the simple [lp]("https://www.cups.org/documentation.php/doc-1.7/man-lp.html") command from CUPS has some options to handle page orientation and margins.

---

### Post by Lady Owl on 2015-01-08
Thanks for the tips, although not solved yet...
I cannot change the design - all I have is a copyrighted pdf-file, which for example pdfmod and bookletimposer can't even handle. It seems probable that the file is password-protected against any modifications. 

Buying a new printer with duplexer does not fit in the budget (or in our home office). I could get on if the pages were off 2mm each, but not this much.

---

### Post by Lady Owl on 2015-01-08
> **schragge said:**
> ```
axi-cache search pdf
``` is even better than *apt-cache*: it sorts results by relevance. But even the simple [lp]("https://www.cups.org/documentation.php/doc-1.7/man-lp.html") command from CUPS has some options to handle page orientation and margins.


Eeerm.... I'm a newbie with CLI, and that man page leaves me confused. (I understand in a very abstract level how composing a command works, but not which parts I really need and how to really get what I want.) There's a switch for landscape, but does it mean the outputted file, the paper or what? No switch for centering mentioned, either. (Not even elsewhere in the CUPS man pages)

---

### Post by tgalati4 on 2015-01-08
Try installing *pdfmod*.  Open a terminal:

```
sudo apt-get install pdfmod
```

Now run it:

```
pdfmod
```

Open a PDF file.  Click on it so that it is highlighted.  Click the rotation button.  Save the file with a new name.  Then try printing the rotated file.

---

### Post by Lady Owl on 2015-01-13
> **tgalati4 said:**
> Try installing *pdfmod*.
As I wrote above, I have already tried pdfmod. It couldn't even open the file - only gives an error message if I try. (When I opened the file with Acrobat reader, it indeed showed that it is a protected file.)

---

### Post by steeldriver on 2015-01-13
I'm not clear what you want to do exactly - would you prefer to translate the second page, but accept rotating it as an option? or do you want to both translate and rotate a particular page?

You can rotate individual pages using pdftk - for example, to rotate the fourth page of a multipage pdf `original.pdf` to the "East" (i.e. +90degrees), writing out other pages unchanged, to a new file `new.pdf`

```

pdftk original.pdf cat 1-3 4E 5-end output newfile.pdf

```

---

### Post by Lady Owl on 2015-01-19
> **steeldriver said:**
> I'm not clear what you want to do exactly

I'll try to explain it in another way. If this was something I could print at work (= in Windows, except the printer there would not need any of this fiddling... but no private printing there, of course) I would simply print the landscape pages on portrait paper *centering* the pages but absolutely *not scaling* to fit. Thus some of the wide margins would fall outside the paper but the planner pages in the center would still fit on the paper. If I could do the same at home, both sides would be printed from the same direction and the faulty offset would match instead of adding up. Then I could cut out the planner pages just fine.

I have 12 files, one for each month, and alltogether of course 365 pages. (This doesn't really save money, but I get the kind of pages I want - the functionality that I want.) 

Is any of those programs able to modify a protected pdf-file? Tried 2 that might have been able to do what I want, but they could not work with it.

---

### Post by tgalati4 on 2015-01-19
What program are you using to print in Windows?  If it is Acrobat (not Acrobat Reader), then perhaps you have the abilitity to rotate the files and resave them in Windows, then email the new files to yourself and try to print within linux.

It doesn't take much time to make a calendar form in *scribus*.  In fact, if you search around, you may find one already made that is close to what you want.  Life is too short to deal with locked forms that you can't modify for your purposes.  That's like finding a recipe on the web with the disclaimer that you are not allowed to modify this recipe.

---

### Post by Lady Owl on 2015-02-11
> **tgalati4 said:**
> What program are you using to print in Windows?  If it is Acrobat (not Acrobat Reader), then perhaps you have the abilitity to rotate the files and resave them in Windows, then email the new files to yourself and try to print within linux.
Hmmm... Well, THAT might work. Not just saving (because when printing in Ubuntu it automatically rotates the pages to match the paper...) but if I could print it as pdf the way I want... Have to try that.

> **tgalati4 said:**
> It doesn't take much time to make a calendar form in *scribus*.  In fact, if you search around, you may find one already made that is close to what you want.  Life is too short to deal with locked forms that you can't modify for your purposes.  That's like finding a recipe on the web with the disclaimer that you are not allowed to modify this recipe.

Nope. None of the free forms are what I like - I've payed for these pages for a reason, and I'm not the one to copy the work of the one-girl-company. (I don't copy my favourite authors books, either!) Nor do I have the energy to learn scribus - and I've also tried to make some pages myself. It's one of those things I'd like to do in theory, but not in practice. Or maybe 15 years ago as a student (when I had more time & energy), but not anymore.

---


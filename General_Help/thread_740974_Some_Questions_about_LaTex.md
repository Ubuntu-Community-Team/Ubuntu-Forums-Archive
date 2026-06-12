---
title: "Some Questions about LaTex"
date: 2008-03-31
forum: General Help
---

### Post by MONODA on 2008-03-31
I recently discovered LaTex and though it was pretty cool. I have seen other people on this forum talk about how they used it for writing reports. I thought I would use it and decided to use Texmaker which is decent but can get annoying. Anyway my questions are, what are the benefits of using LaTex compared to WYSIWYG word processors like OOo writer? Also, what do you recommend I use to write LaTex? and is there anyway to save as .doc format since my school wont accept anything else?

---

### Post by Slushdoot on 2008-03-31
I use LyX as a frontend for LaTeX so I can only really commend on that.  The benefit from using a program like it, rather than a WYSIWYG,  is that you don't have to futz around with formatting while you write.  The styles are pre-defined and you simply have to tell it which part is which part.  It makes it easier to use LaTeX/TeX to create nice-looking documents.  I usually export to .pdf which everybody should be able to open these days.  If they're very strict about it, you might look at a utility called TeX2Word.  I haven't used it so I cannot attest to its ease of use or effectiveness. :)

---

### Post by MONODA on 2008-03-31
alright thanks, btw is LyX GUI or CLI??

---

### Post by Slushdoot on 2008-03-31
GUI, thought it depends on a lot of CLI tools to do the gruntwork behind the scenes.

---

### Post by MONODA on 2008-03-31
I just checked out tex2word, you need to buy it :( anyway, I know that you can make really good mathmatical equations with LaTex but is there any benefit to it for someone who just needs word processing and the ability to ad footnotes and page numbers?

---

### Post by Slushdoot on 2008-03-31
It's fast, lightweight, and creates great-looking documents.  It runs on Windows, Linux, and OS X.  You can use BiblioTeX for easy bibliographic work when composing papers.

As with anything it has its positives and negatives.  If OO.o does everything you need and you're happy with it, there's little reason to switch and encounter the hassles associated with people who won't accept .pdf. :p

---

### Post by MONODA on 2008-03-31
yeah I guess your right,  I knew i wasnt going to switch over to it now but I just wanted to know why people use it.
> 
It's fast, lightweight, and creates great-looking documents. It runs on Windows, Linux, and OS X. You can use BiblioTeX for easy bibliographic work when composing papers.
I really dont understand what people mean by that it makes good looking documents, could someone clear that up b/c I dont notice much of a difference raelly.

---

### Post by Slushdoot on 2008-03-31
TeX was developed by Donald Knuth to perform typesetting in such a way that it was attractive to the eye.  It tries to optimize a lot of things, including the number of letters per line, the number of words per line, the distance between letters and words in a line, the place to break a word when using hyphenation, and the actual typefaces used.  Knuth spent 10 years studying the problem of computer typesetting before finally being satisfied with his result.

To read more about the interesting history of TeX you should check out the Wikipedia article for it: [http://en.wikipedia.org/wiki/TeX](http://en.wikipedia.org/wiki/TeX)
:)

---

### Post by MONODA on 2008-03-31
Ok thanks for clearing that up, I guess I wont be using LaTex to word process untill my reports become more complicated. Anyway, I have decided to use it to create a document which needs to include equations and some bitmap images. I heard that you can create bitmaps with LaTex, how can I do that?

---

### Post by Slushdoot on 2008-03-31
I don't really know much about exporting as bitmaps, but on a somewhat related note [OOoLatex](http://ooolatex.sourceforge.net/) might be of interest to you.

---

### Post by Whiffle on 2008-03-31
Check out kile while you're looking at LaTeX stuff, its very handy.

As far as advantages

-writing mathematical stuff is much easier.  Have you tried the formula writer in Office 2007?  It is absolutely horrid in comparison.  Sure, no learning curve whatsoever but it takes forever to make anything.

-it doesn't try to predict what you want to do while you type.  

-long documents are easier to handle.  Ever write a paper, then decide to add a picture somewhere and instantly all your formatting is messed up?  It doesn't happen with latex.  It uses a set of rules that have been developed over the years (it has its roots in the 70s) to move everything around to where it should be.

-references are easy.  Latex keeps track of numbering of figures, tables, sources, etc.  so you don't have to number them yourself.

-latex prints nicer with more regard to how things should actually be rendered (spacing, word pairs).  Sure, the differences are small, but its the difference between something that looks like crap and something that looks professional.  [http://nitens.org/taraborelli/latex](http://nitens.org/taraborelli/latex)

---

### Post by MONODA on 2008-03-31
thanks for that :D. I will most likely use LaTex in the future when I do not need 99% compatibility with MS Word.

---

### Post by frisket on 2008-04-09
> **MONODA said:**
> I recently discovered LaTex and though it was pretty cool. I have seen other people on this forum talk about how they used it for writing reports. I thought I would use it and decided to use Texmaker which is decent but can get annoying. Anyway my questions are, what are the benefits of using LaTex compared to WYSIWYG word processors like OOo writer? Also, what do you recommend I use to write LaTex? and is there anyway to save as .doc format since my school wont accept anything else?

For benefits wrt wordprocessing, see the Preface to my book _Formatting Information_
[http://latex.silmaril.ie/formattinginformation/preface.html](http://latex.silmaril.ie/formattinginformation/preface.html)

LaTeX *is* WYSIWYG, far more so than any wordprocessor. But it's asynchronous, not synchronous.

There are several utilities to convert LaTeX to .doc format, but the problem is that LaTeX is more powerful than a wordprocessor, so there are things it can do which simply can't be represented in a .doc file. The best way is to cheat: use TeX4ht to convert your document to XHTML, do any manual edits to tidy things that an automated conversion can't do, check validity, and then rename the file to end with .doc -- Word will open it, and provided it is a valid XHTML file, will display it as if it was a real .doc file. 

///Peter

---


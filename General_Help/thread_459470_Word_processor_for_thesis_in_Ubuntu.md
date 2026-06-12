---
title: "Word processor for thesis in Ubuntu"
date: 2007-05-30
forum: General Help
---

### Post by vav on 2007-05-30
I'm looking at word processors to write a thesis in. We've used Frame maker from Adobe as yet. It works great for styling, cross-referencing and handling large documents. However, active development I believe has stopped, and hence the user interface is not getting any better.

I guess this is a much discussed topic, which is probably why I have a hard time getting any real  info. I'm counting on the experience of you guys!

I found an article comparing Framemaker and Openoffice, but it's old:
[http://www.newsforge.com/article.pl?sid=04/10/04/150207](http://www.newsforge.com/article.pl?sid=04/10/04/150207)
edit: Another article: [http://www.dwheeler.com/blog/2007/04/18/](http://www.dwheeler.com/blog/2007/04/18/)

I want to stick to Ubuntu options if possible. At present I run XP in Virtualbox to support Framemaker.

The obvious first choice is open office. The only issue is that I dont have any support on this topic. No one around uses openoffice for this.  (I agree latex gives probably the best output, but altho I'm geeky I'd rather concentrate on my thesis while writing it than compiling code/dealing with unintuitive interfaces). 

How does the latest version of Openoffice do on the following:
1> EASY Controllable and intuitive Auto Numbering of Tables and Figures
2> EASY cross-reference insertion (and auto-update of the same if the ref changes)
3> Control over fonts and alignment while doing the automagical numbering
4> Handling large documents with a lot of figures efficiently
5> EASY Custom Styling of documents, saving styles for use in later sessions
6> CLEAN equation editing and output (I've heard concerns about this)
7> Automatic contents generation with changes in chapter names reflected in index
8> WYSIWYG pdf output for ALL parts, including equations, figures, numbers

Any other editor that does these better?

---

### Post by Kent84 on 2007-05-30
There are some WYSIWYG latex editors out there which makes it a lot easier. Openoffice has very good cross-referencing and auto-formatting features which almost tempted me to do my thesis in that.... there are loads of tutorials at their website [www.openoffice.org](www.openoffice.org) which can teach you all of this. I have used solely openoffice, even before I switched to ubuntu, for the past 2 years and have had no regrets.

---

### Post by matog on 2007-05-30
Latex!!! It´s very easy to install (it´s in the repos) and, once you´re familiar to it, it´s the best!

---

### Post by Blender on 2007-05-30
Definitely LaTeX. Buy a book, learn the basics and you're ready.

But since you ask about word processor (which LaTeX is not), I'd suggest either Lyx 
(a WYSIWYG LaTeX editor) or OpenOffice.org. 

But please note that there's nothing better than LaTeX (and DocBook) in terms of 
cross-referencing, citing, etc, simply because you code it the way you want it, 100% 
control. And there are *tons* of ready-to-use packages for almost anything you can
think of.

One more thing: since you said "we've used...", are there more people involved? If 
so, LaTeX is a good choice, as its files are plain text documents that can be version
controlled very easily.

If you're going to write math, then there's only LaTeX. Period.

HTH.

---

### Post by vav on 2007-05-31
Unfortunately I cant expect my advisor and other students to learn latex for my benefit. they need to be able to edit this document too. An easier option is required. 

So according to Kent84 odf is sufficient to write a thesis grade document, possibly with the help of ooolatex.sourceforge.net macros for equations...?

I dont understand why openoffice doesnt support tex as a file format. one could start with a tex template, edit text and figures in openoffice and save as a tex file? That's a separate issue though...

---

### Post by Blender on 2007-05-31
If you want LaTeX that way, why don't you try Lyx ([http://www.lyx.org]("http://www.lyx.org"))?

---

### Post by Firminator on 2007-05-31
I'm going to do my First degree in Physics & Engineering  can anyone of you recommend a word processor which is good for both mathematical writing and doesn't cause much trouble with right to left writing (i Need it for Hebrew)

i tried Open office but I'm not over enthusiastic about it. Unfortunately, the only the only word processor I was able to use comfortably was MS Word.

thank you.

---

### Post by vav on 2007-05-31
Firminator, please start a separate thread about the right to left issue. You'll get more responses that way.

I can use Lyx, but no one else that needs to edit the thesis will, since it doesnt look remotely like either Openoffice/MS Word or Framemaker :(

So I guess back to my original question: Any big problems writing in openoffice as long as equations are written with latex?

---

### Post by 56phil on 2007-05-31
vav, 

I'm not a fan of Lyx. It generates non-standard code. I use Kile to edit my latex documents and have no regrets. I believe that as a document becomes larger and more complicated latex makes more sense. 

Good luck on your thesis.

---

### Post by vav on 2007-06-05
Is there a way to convert latex to another editable format such as .doc? 
Would the best option be to generate a pdf and edit with Adobe Acrobat?
I figure if I can continue to write/incorporate changes in latex, and others could edit a converted document, it could be the best solution...

---

### Post by Kent84 on 2007-06-06
@Vav: Why would you want others to edit your thesis??? If you want file/files easily edited by many users with version histories, etc, I suggest you setup a wiki server. For a few users altering a TeX file, CVS works good too. If you want others to view your thesis for proof reading or to make notes, then send them your thesis in a PDF and then they can use adobe to do that.

---

### Post by Extrudedaluminiu on 2007-06-06
I've had a lot more success with TeXmacs than LyX these days; you can export and import HTML, which other people can also edit.

---

### Post by AnRa on 2007-06-06
> **vav said:**
> So I guess back to my original question: Any big problems writing in openoffice as long as equations are written with latex?You can also write formulas using OpenOffice.org without needing LaTeX.

---


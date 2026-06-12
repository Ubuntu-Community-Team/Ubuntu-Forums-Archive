---
title: "Import latex equations in libreoffice/word"
date: 2014-02-12
forum: General Help
---

### Post by youris on 2014-02-12
Hi,

  I know that question has been asked many times, but thinks change and it's hard to find "the solution".
I wrote a 10 pages document with Lyx/Latex, with many equations, for somebody's thesis written in word format.
Converting to html then importing in writer/word works for text, but not for equations. OOolatex or Texmaths give images, not real equations.


Does anybody have a solution to convert .tex to .doc, or just equations? 
A solution on linux would be fine, but I take any advice. 
I haven't tried latex2word (word extension to import latex documents) yet because I don't have word, but I'll try soon.

Thanks by advance


______________________
Please excuse my english, I am french.

---

### Post by dragonfly41 on 2014-02-12
For desktop publishing .. mixing text and LaTex frames .. try Scribus

[http://scribus.net/canvas/Scribus](http://scribus.net/canvas/Scribus)

Try New Document > Insert > Render frame (for LaTex input).

There is also Lyx Document Processor in Ubuntu Software Centre.

[Later edit]
I see that you already use Lyx.

---

### Post by youris on 2014-02-13
I didn't manage to convert my latex document to a word document, or to convert latex equation to word equation with scribus.
I think you misunderstood me, my document is already written in latex format. 

What I want to do is just convert my .tex file to a .doc file (or other oppenoffice format), especially for equations.

I don't want my equations to become images, but real word/OO equations.

---

### Post by dragonfly41 on 2014-02-13
I had in mind exporting your Scribus doc as either PDF or SVG.

Scribus allows you to paste LaTex into Render Frame .. and mix with text frames and image frames

then File > Export > Save As as EPS, PDF, Image or SVG

However if you prefer to convert LaTex to Doc format try this

[http://community.dur.ac.uk/p.j.heslin/Software/Latex/latex2doc.php](http://community.dur.ac.uk/p.j.heslin/Software/Latex/latex2doc.php)

or read here for tips ... (google search "latex2doc")

[http://ubuntuforums.org/showthread.php?t=1033441](http://ubuntuforums.org/showthread.php?t=1033441)

[Later edit] You might hit problems with that last link.

[http://tug.org/applications/tex4ht/mn-upgrade.html](http://tug.org/applications/tex4ht/mn-upgrade.html)

As an alternative you could try this .. [http://latex2rtf.sourceforge.net/](http://latex2rtf.sourceforge.net/)  .. but note the warnings about possible errors in conversion.

---

### Post by youris on 2014-02-13
Thank you for your help, but the solutions you propose give pictures or rtf. 
Pictures --> not what I want
rtf        --> bad support of formulas
I have already tried tex4ht, the render is really good for html, but converting into .doc gives bad formulas.
Your solutions might be useful for people who doesn't need formulas conversion.
 
I finally tried Tex2Word, and it works great! I had just to correct some details, but it gives real equations.
[http://www.chikrii.com/products/tex2word/](http://www.chikrii.com/products/tex2word/)

This solution is paying, but the trial version (one month) is free.

---


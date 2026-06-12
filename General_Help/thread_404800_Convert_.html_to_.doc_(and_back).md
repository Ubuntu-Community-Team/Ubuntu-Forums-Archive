---
title: "Convert .html to .doc (and back)?"
date: 2007-04-08
forum: General Help
---

### Post by jfinkels on 2007-04-08
Hello people. I am going to be working on a project that may require us to convert HTML to Word documents and back (if possible!). I was wondering if anyone has heard of / knows any utility that has this functionality. I have seen wvWare ([http://wvware.sourceforge.net/](http://wvware.sourceforge.net/) ... although it says that it has been deprecated in favor of AbiWord's command-line functionality) which converts to html, and I have seen *html2text* which converts from html to text.

Just wanted to see if anyone has any experience converting from HTML to .doc, and also if anyone thinks it is possible or easy to convert the other way.

---

### Post by WiseElben on 2007-04-09
It really depends on the complexity of the HTML involved. You can just copy and paste HTML from a browser into OpenOffice Word and save it as a .doc easily. OO Word also converts .doc to .html. Just "Save As" and add .html at the end or choose HTML under "File Type."

---

### Post by aysiu on 2007-04-09
I don't know how to use this, but from what I've heard, you should be using LaTeX.
[http://www.latex-project.org/](http://www.latex-project.org/)

---

### Post by jfinkels on 2007-04-09
> **WiseElben said:**
> It really depends on the complexity of the HTML involved. You can just copy and paste HTML from a browser into OpenOffice Word and save it as a .doc easily. OO Word also converts .doc to .html. Just "Save As" and add .html at the end or choose HTML under "File Type."

Unfortunately, we will need to convert a large quantity of word documents, so we are really looking for a command-line utility, for use in a script! :P

> **aysiu said:**
> I don't know how to use this, but from what I've heard, you should be using LaTeX.
[http://www.latex-project.org/](http://www.latex-project.org/)

I have actually used LaTeX before! LaTeX has a HUGE amount of converters out there for a great number of formats. As much as I would not really like to convert from .doc -> .tex -> .html and back, I may look into this as a possibility.

By the way, in my search, I found this very old page. A lot of broken links, but it's a starting point, I guess :| ([http://www.w3.org/Tools/Word_proc_filters.html)](http://www.w3.org/Tools/Word_proc_filters.html)).

Thanks, guys :) Does anyone else have any ideas?

---

### Post by frisket on 2007-04-09
> **jfinkels said:**
> I am going to be working on a project that may require us to convert HTML to Word documents and back (if possible!). I was wondering if anyone has heard of / knows any utility that has this functionality.

Yes, but not in any way that would be useful to you. Round-trip conversion from SGML to Word and back again was possible with Microsoft's own SGML Author for Word, which despite its name was a convertor, not an editor. It really could take an SGML document (including, of course, HTML) and convert it to a .doc file with Named Styles, let non-technical people edit it (with Named Styles, natch) and then convert it losslessly back to SGML. I had a copy, and reviewed it in my book on SGML and XML Tools. Unfortunately, just as XML was becoming popular, Microsoft dropped it on the floor and lost the plot.

However, the holy grail of circular conversion is not lost. It depends on where you enter the loop. Essentially all you need to do is write an XSLT transformation from Word's XML format to HTML and back again. However, this will only work if your users/editors/authors stick to Named Styles that you invent for the purpose and distribute in a template. The slightest variation from this and all bets are off.

///Peter

---


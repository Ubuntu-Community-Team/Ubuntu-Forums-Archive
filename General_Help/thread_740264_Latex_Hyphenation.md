---
title: "Latex Hyphenation"
date: 2008-03-30
forum: General Help
---

### Post by rogeriovinhal on 2008-03-30
I've installed all the texlive packages, including the extra, but I can't use any hyphenation for portuguese language.

This is what I get when I compile:
```

Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.

Package babel Warning: No hyphenation patterns were loaded for
(babel)                the language `Portuguese'
(babel)                I will use the patterns loaded for \language=0 instead.

```

Are these the only hyphenation patterns I can get with the ubuntu livetex package? Only english and dummu languages?

---

### Post by araz on 2008-03-30
Hi,
Install this package  texlive-lang-portuguese.

:)

---

### Post by rogeriovinhal on 2008-03-30
> **araz said:**
> Hi,
Install this package  texlive-lang-portuguese.

:)

Oh... Thanks... :)

I've been searching in apt for 'latex'. Damn that package that doesn't even have the word 'latex' in its description.

---

### Post by frisket on 2008-04-09
That's because it's not just for LaTeX, but for plain TeX, ConTeXt, Texinfo, etc, etc as well.

---

### Post by Belerophon on 2008-07-20
Hi!
Quick thing...I saw somewhere on the web that we should use the package fontenc, with the option T1, so that latex could do the correct hyphenation of the text...is this true?
When I use it my pdf output looks different, the characters look a little blurry...
(I'm using ubuntu, and texlive; using latex, dvips and ps2pdf, not pdflatex)

What does the fontenc package do anyway?

Thanks!

---

### Post by hugmenot on 2008-07-21
As far as I know fontenc does not affect hyphenation at all. Fontenc is used to specify how the glyphs in the font are encoded. Type 1 PostScript fonts are T1, and you should use T1 if you compile to PDF with PDFLaTeX or somesuch. You can only embed PostScript font with T1 properly. This also helps to select and copy text from the resulting PDF properly.

The best font family for T1 font encoding is Latin Modern (\usepackage{lmodern}), but cm-super works too.

---

### Post by Belerophon on 2008-07-23
> **hugmenot said:**
> As far as I know fontenc does not affect hyphenation at all. Fontenc is used to specify how the glyphs in the font are encoded. Type 1 PostScript fonts are T1, and you should use T1 if you compile to PDF with PDFLaTeX or somesuch. You can only embed PostScript font with T1 properly. This also helps to select and copy text from the resulting PDF properly.

The best font family for T1 font encoding is Latin Modern (\usepackage{lmodern}), but cm-super works too.

Ok, thanks...so I should get rid of the \usepackage[T1]{fontenc} from my files, since I do not use pdflatex...

Thanks again.

---

### Post by Belerophon on 2008-07-23
> **hugmenot said:**
> As far as I know fontenc does not affect hyphenation at all. Fontenc is used to specify how the glyphs in the font are encoded. Type 1 PostScript fonts are T1, and you should use T1 if you compile to PDF with PDFLaTeX or somesuch. You can only embed PostScript font with T1 properly. This also helps to select and copy text from the resulting PDF properly.

The best font family for T1 font encoding is Latin Modern (\usepackage{lmodern}), but cm-super works too.

In my search through the web trying to find a way to use Times fonts in latex :), I found this page:
[http://dsanta.users.ch/resources/type1.html](http://dsanta.users.ch/resources/type1.html)

So, it seems that the fontenc is necessary to hyphenate words with  accented characters. 

This page also explains how to use times fonts and how to obtain good quality pdf's(at least under linux...I always noticed the difference between the pdf's I produced with latex and other ones...but not any more :)

Thanks.

---

### Post by hugmenot on 2008-07-23
No, you should keep it in even if you use dvips + ps2pdf. The end format matters.
PDF likes T1 Postscript fonts. Printers like T1 PostScript fonts, too.

Just switch your font to lmodern or cm-super.

---

### Post by hugmenot on 2008-07-23
> **Belerophon said:**
> In my search through the web trying to find a way to use Times fonts in latex :), I found this page:
[http://dsanta.users.ch/resources/type1.html](http://dsanta.users.ch/resources/type1.html)

So, it seems that the fontenc is necessary to hyphenate words with accented characters. 

This page also explains how to use times fonts and how to obtain good quality pdf's(at least under linux...I always noticed the difference between the pdf's I produced with latex and other ones...but not any more :)

The page contains some obsolete information. The EC fonts are not the current solution, Latin Modern is.

I didn&#8217;t know that fontenc affects hyphenation of accented characters. Good to know.

BTW, why use dvips? It&#8217;s so old-school.

---

### Post by Belerophon on 2008-07-23
> **hugmenot said:**
> The page contains some obsolete information. The EC fonts are not the current solution, Latin Modern is.

I didn’t know that fontenc affects hyphenation of accented characters. Good to know.

BTW, why use dvips? It’s so old-school.

Well, my first attempt with LaTeX was with pdflatex, but it didn't work with some vectorial picture that I had to include in the doc. An EPS file...so I switched to latex.

You must have noticed that I'm not an expert in these things lol, but I followed the instructions in that page and now I have this in the preamble of a doc:
```

...
\usepackage[T1]{fontenc}
\usepackage{ae, aecompl}
\usepackage{pslatex}
...

```
and using the commands:

```

dvips -t a4 -Ppdf -z template.dvi
ps2pdf -dPDFSETTINGS=/screen template.ps

```

What do you think I should modify to update me to the "current solution"??

Thanks!

---

### Post by hugmenot on 2008-07-23
> **Belerophon said:**
> Well, my first attempt with LaTeX was with pdflatex, but it didn't work with some vectorial picture that I had to include in the doc. An EPS file...so I switched to latex.


Ah ok. PDFLaTeX supports PDF for vector graphics. Just convert your EPS files to PDF.
You'll see the compilation is a lot faster. And PDFTeX has cool typographic features.

To convert use "epstopdf *.eps"

> 
You must have noticed that I'm not an expert in these things lol, but I followed the instructions in that page and now I have this in the preamble of a doc:
```

...
\usepackage[T1]{fontenc}
\usepackage{ae, aecompl}
\usepackage{pslatex}
...

```


make that:
```

...
\usepackage[latin1]{inputenc}    % you can enter úôç etc directly
\usepackage[T1]{fontenc}        
\usepackage[portuguese]{babel}
\usepackage{mathptmx}  % or \usepackage{lmodern}, or \usepackage{charter}
...

```
The last line chooses the font family. If you really want to use Times, then use mathptmx. But there are many good looking alternatives, like Charter BT. Look here: [http://www.tug.dk/FontCatalogue/](http://www.tug.dk/FontCatalogue/)

> 

and using the commands:

```

dvips -t a4 -Ppdf -z template.dvi
ps2pdf -dPDFSETTINGS=/screen template.ps

```

Just use 
```

pdflatex template.tex

```
that&#8217;s the current way of doing things.

---

### Post by Belerophon on 2008-07-23
Thanks a lot for the explanation :D. I will change my "method" ;)

---


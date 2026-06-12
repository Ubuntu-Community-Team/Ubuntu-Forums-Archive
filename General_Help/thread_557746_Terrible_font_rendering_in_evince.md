---
title: "Terrible font rendering in evince"
date: 2007-09-23
forum: General Help
---

### Post by LondoMollari on 2007-09-23
Hi!

I'm having a problem with evince... the problem does not apply to xpdf or acroread though.
I have tried to change the font rendering in System->Preferences->Font, to no avail...
I'm running Ubuntu 7.04..

I'll attach two screenshots; one showing evince and the other acroread
Any help is much appreciated! :p

---

### Post by bogoliubov on 2007-09-23
> **LondoMollari said:**
> Hi!

I'm having a problem with evince... the problem does not apply to xpdf or acroread though.
I have tried to change the font rendering in System->Preferences->Font, to no avail...
I'm running Ubuntu 7.04..

I'll attach two screenshots; one showing evince and the other acroread
Any help is much appreciated! :p

What options do you have set System-Preferences-Font ?

---

### Post by LondoMollari on 2007-09-23
I have tried with "Best shapes" (the default) and Subpixel Smoothing (LCD)...it makes no difference in evince...

anyway.. I just noticed that evince displays .dvi files and pdf files not created with LateX perfectly... now I'm really confused

---

### Post by hugmenot on 2007-09-23
That's clear case of shitty T3 fonts in a pdf converted from a Latex .dvi.
In the past those PDFs also displayed really poorly in Acroread.
The person should have used \usepackage[T1]{fontenc} to use the better Postscript kind of fonts. Even better nowadays pdflatex should be used instead of the obsolete and cumbersome dvi&#8594;ps&#8594;pdf method.

Evince is not to be blamed for this.

---

### Post by LondoMollari on 2007-09-23
Ok thanks! I'll remember that when I make my own PDFs from latex ;-)

---

### Post by f03el on 2007-09-24
> **hugmenot said:**
> That's clear case of shitty T3 fonts in a pdf converted from a Latex .dvi.
In the past those PDFs also displayed really poorly in Acroread.
The person should have used \usepackage[T1]{fontenc} to use the better Postscript kind of fonts. Even better nowadays pdflatex should be used instead of the obsolete and cumbersome dvi&#8594;ps&#8594;pdf method.

Evince is not to be blamed for this.

\usepackage[T1]{fontenc} and pdflatex doesn't help me. This gives exactly the same poor font rendering as LondoMollari showed. I found something about a bug in Poppler used in Evince: [Bug #92296 in poppler (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/92296").

---

### Post by hugmenot on 2007-09-24
If you open the file in Acroread and press Ctrl-D, in the fonts Tab, what kind of fonts does it list? Type 1 or Type 3?

---

### Post by f03el on 2007-09-24
These fonts are listed in Adobe Reader:

_Type 1_
CMMI12
CMMI8
CMR12
CMR8
CMSY10
CMSY8

_Type 3_
F16
F18
F27

The same fonts seem to be listed in Evince but the type 3 fonts have no names there.

---

### Post by hugmenot on 2007-09-24
Hmm. Could you post a minimal test case of the tex source (just the preamble and a sentence)?

---

### Post by f03el on 2007-09-27
Sure. Would be fun to see what it looks like when someone else pdflatex this:
```
\documentclass[a4paper,12pt]{article}

\usepackage[T1]{fontenc}
\usepackage[swedish]{babel}
\usepackage{ucs}
\usepackage[utf8x]{inputenc}

\usepackage{fancyhdr}
\usepackage{graphicx}

\title{Labrapport - Zeemaneffekt}

% Stuff here cutted

\begin{document}
\section{Inledning}
Laborationen går ut på att studera Zeemaneffekten, vilken uppstår då en atom befinner sig i ett magnetfält. Denna effekt leder till ytterligare uppsplittring av de redan finstrukturerade energinivåerna. Vidare studerar vi de olika polarisationerna som det emitterade ljuset har i olika riktningar.

% And some more cutting here

\end{document}

```

---

### Post by hugmenot on 2007-09-27
Alright, it's because you use Unicode. I never do that. Apparently there are some interactions with the mapping from Unicode to font encoding. When I kicked out fontenc and ucs it worked fine.

```
\documentclass[10pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[swedish]{babel}

\title{Labrapport - Zeemaneffekt}
```

You might get better results with lmodern (Latin Modern), beacause in that package the swedish diacritics are one character and not composed, i.e., a+°. In the text, when I copy the first few words with the default font, it pastes like

```
Laborationen gar ut pa att
```

with lmodern /and/ the fontenc line back after it

```
Laborationen går ut på att
```

Hence this is my recommended preamble:
```
\documentclass[10pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[swedish]{babel}
\usepackage{lmodern}
\usepackage[T1]{fontenc}

\title{Labrapport - Zeemaneffekt}
```

---

### Post by f03el on 2007-09-27
Wow! That worked. Thanks a lot for your quick anwers! :KS
*Writing down keyword lmodern*

Too bad that it still exists pdfs out there which look ugly in Evince.

---


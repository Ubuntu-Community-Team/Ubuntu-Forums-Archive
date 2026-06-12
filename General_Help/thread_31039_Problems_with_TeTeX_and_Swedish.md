---
title: "Problems with TeTeX and Swedish"
date: 2005-05-01
forum: General Help
---

### Post by Grul on 2005-05-01
I am trying to use the suggested LaTeX system on Ubuntu, and it works nicely if I try to write an english document. However, if I try to write one in swedish the LaTeX system goes haywire and starts to spew out error messages. I've written the document according to what I could find on the internet, as such:

```

\documentclass[12pt,a4paper]{article}
\usepackage[swedish]{babel}
\usepackage[T1]{fontenc}
\usepackage[latin1]{inputenc}

\begin{document}
Detta är ett svenskt dokument.
\end{document}

```

LaTeX prints lots of error messages such as

! LaTeX Error: Command \textcurrency unavailable in encoding T1.
! LaTeX Error: Command \textyen unavailable in encoding T1.

and screws up all the umlauts in the resulting .dvi file. Is this due to missing fonts? I've installed all the three tetex packages. I've googled around for this a good while and have found nothing on this particular problem.

---

### Post by Olli on 2005-05-01
[QUOTE=Grul]I am trying to use the suggested LaTeX system on Ubuntu, and it works nicely if I try to write an english document. However, if I try to write one in swedish the LaTeX system goes haywire and starts to spew out error messages. I've written the document according to what I could find on the internet, as such:

```

\documentclass[12pt,a4paper]{article}
\usepackage[swedish]{babel}
\usepackage[T1]{fontenc}
\usepackage[latin1]{inputenc}

\begin{document}
Detta är ett svenskt dokument.
\end{document}

```

LaTeX prints lots of error messages such as

! LaTeX Error: Command \textcurrency unavailable in encoding T1.
! LaTeX Error: Command \textyen unavailable in encoding T1.

and screws up all the umlauts in the resulting .dvi file. Is this due to missing fonts? I've installed all the three tetex packages. I've googled around for this a good while and have found nothing on this particular problem.[/QUOTE]


I have ceased to use teTeX - I am using instead vtex (CTAN/pub/tex/systems/vtex) - but I have some experience with teTeX. The problem with teTeX used to be that there was no hyphenation file for swedish (sehyph.tex), but it was to be downloaded separately from CTAN.
As for your suspected missing fonts - my header is similar with the exception that I also have defined the font - in my case lm

\renewcommand{\familydefault}{lmss}

Hope this helps you.

---

### Post by ow50 on 2005-05-01
If you're running Hoary, you're probably using UTF-8 as your system's character encoding. If so,  you should also use UTF-8 in latex. See if the following works:
```
\documentclass[12pt,a4paper]{article}

\usepackage{ucs}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[swedish]{babel}

\begin{document}
Detta är ett svenskt dokument.
\end{document}
```

---

### Post by Grul on 2005-05-02
[QUOTE=ow50]If you're running Hoary, you're probably using UTF-8 as your system's character encoding. If so,  you should also use UTF-8 in latex. See if the following works:
```
\documentclass[12pt,a4paper]{article}

\usepackage{ucs}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[swedish]{babel}

\begin{document}
Detta är ett svenskt dokument.
\end{document}
```[/QUOTE]

When I try that it says that ucs.sty cannot be found (if I uncomment that line, it can't find utf8.def instead).

It is really frustrating that there seems to be so many different LaTeX configurations. Is there no uniformity at all in LaTeX? Well, maybe I should dump TeTeX in favor for something else just to try it out.

---

### Post by ow50 on 2005-05-02
[QUOTE=Grul]When I try that it says that ucs.sty cannot be found[/QUOTE]
$ sudo apt-get install latex-ucs latex-ucs-uninames

There's a couple other latex-ucs-* packages, but those should be enough.

[QUOTE=Grul]It is really frustrating that there seems to be so many different LaTeX configurations. Is there no uniformity at all in LaTeX?[/QUOTE]
With the different configurations LaTeX works on all platforms and all character encodings.

---

### Post by Grul on 2005-05-03
It works now. Thanks for your help!

---

### Post by kalindriv on 2005-05-05
[QUOTE=ow50]$ sudo apt-get install latex-ucs latex-ucs-uninames

There's a couple other latex-ucs-* packages, but those should be enough.


With the different configurations LaTeX works on all platforms and all character encodings.[/QUOTE]

Thanks a lot!!! I needed it to use easily the Italian language!!!  :smile:

---

### Post by Humboldt on 2005-05-21
[QUOTE=ow50]If you're running Hoary, you're probably using UTF-8 as your system's character encoding. If so,  you should also use UTF-8 in latex. See if the following works:
```
\documentclass[12pt,a4paper]{article}

\usepackage{ucs}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[swedish]{babel}

\begin{document}
Detta är ett svenskt dokument.
\end{document}
```[/QUOTE]

When I try this I get the following message: 
/usr/share/texmf/tex/latex/base/fontenc.sty|| I can't find file `ecrm1000'. ...ljfour; mag:=1; nonstopmode; input ecrm1000 
/usr/share/texmf/tex/latex/base/fontenc.sty|| Emergency stop.
/usr/share/texmf/tex/latex/base/fontenc.sty|95 error| Font T1/cmr/m/n/10=ecrm1000 at 10.0pt not loadable: Metric (TFM) file not found

What can I do to sort out this problem

Thanks for any help

---

### Post by ow50 on 2005-05-21
[QUOTE=Humboldt]When I try this I get the following message: 
/usr/share/texmf/tex/latex/base/fontenc.sty|| I can't find file `ecrm1000'. ...ljfour; mag:=1; nonstopmode; input ecrm1000 
/usr/share/texmf/tex/latex/base/fontenc.sty|| Emergency stop.
/usr/share/texmf/tex/latex/base/fontenc.sty|95 error| Font T1/cmr/m/n/10=ecrm1000 at 10.0pt not loadable: Metric (TFM) file not found[/QUOTE]
Try installing package "tetex-extra".

---

### Post by Humboldt on 2005-05-22
Thank you!
You gave me the solution. Now it works,

---

### Post by kalle314 on 2005-08-02
Can this be done in another way?

Everything works for me when i include the packages

\usepackage{ucs}
\usepackage[utf8]{inputenc}

but I do normally include 

\usepackage[latin1]{inputenc}

I would prefer not having to change all my old files, and files I get from other people, to include different packages (and maybe having to change them back if they are to run on a different system).

---

### Post by kalle314 on 2005-08-03
I found an alternative solution here:
[http://lists.gnu.org/archive/html/help-gnu-emacs/2003-12/msg00680.html](http://lists.gnu.org/archive/html/help-gnu-emacs/2003-12/msg00680.html)

- open the file and save it as latin1 (C-x C-m f latin-1).

This works fine for me.

---


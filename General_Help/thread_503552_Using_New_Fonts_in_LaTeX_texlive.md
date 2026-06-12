---
title: "Using New Fonts in LaTeX/ texlive"
date: 2007-07-18
forum: General Help
---

### Post by jadeshade on 2007-07-18
I installed texlive-fonts-extra for its (guess what) extra fonts, but I'm having trouble using them.  In the .tex file I have the lines:
```
\usepackage[T1]{fontenc}
\usepackage{calligra}
```
so I can use the font 'calligra'.  It's listed in the package description from synaptic (so I know it's there).  However, when I 'compile' it with pdflatex, it errors out telling me there's no tfm file.  Anyone know what to do/ have this problem before (the both of you that use tex)?

---

### Post by dgriffi on 2007-09-05
I have noticed this problem too.  I've submitted a bug report about this.  In the meantime, go to [http://www.tug.org/svn/texlive/trunk/Master/texmf-dist/tex/latex/fundus/calligra.sty?view=log&pathrev=945](http://www.tug.org/svn/texlive/trunk/Master/texmf-dist/tex/latex/fundus/calligra.sty?view=log&pathrev=945) and grab calligra.sty.  Then go to [http://tug.ctan.org/tex-archive/fonts/calligra/](http://tug.ctan.org/tex-archive/fonts/calligra/) and get the two .mf files there.  Put these in the same directory as your .tex file or somewhere standard where LaTeX can find it.  Then the following test file will work:

\documentclass[12pt,pdftex]{article}
\usepackage[T1]{fontenc}
\usepackage{calligra}
\begin{document}
\calligra
This is a test of a calligraphy font.
\normalfont
\end{document}

---

### Post by andresv on 2007-09-11
I need to use mathabx fonts in my LaTeX documents. mathabx contains many mathematical symbols I need.

TeTeX used to have the package mathabx - I was astonished to see that TexLive does not include mathabx! There is no mention to mathabx in any of the math- or font-related packages in TexLive.

:confused:

Does anyone know where to find packages that include the mathabx fonts for TexLive?

Thanks! :)

---

### Post by bertram_wooster on 2008-02-27
This may be a little late, but I will post all the same so others might benefit. I cannot guarantee this will work, but it worked for me.

The package is available here:

[http://www-math.univ-poitiers.fr/~phan/metafont.html#mathabx](http://www-math.univ-poitiers.fr/~phan/metafont.html#mathabx)

You should download the .me package. As for installing it, this is what I tried partly from reading install instructions partly from guesswork. The reason the guesswork is needed is that the file structure for tex changes from install to install.

I located the source branch of tex, For me this was '/usr/share/texmf-texlive/fonts/source' (I have ubuntu 7.10 and I installed tex with apt-get). 

To find the source files I ran:

$ locate .mf

This finds all files containing the string '.mf'. The vast majority of these should be in subfolders of the source branch. From here on I shall call this ${TEXMF}/fonts/source, where ${TEXMF} is the root folder for all the other tex files we need.

I chose a suitable location below the level of ${TEXMF}/fonts/source for my .mf files. For me this was in '${TEXMF}/fonts/source/public/mathabx', which I needed to create. I then copied the .mf files from the package source folder to this folder.

Next I created the folder ${TEXMF}/tex/latex/mathabx, and copied the .sty file and the .dcl file there.

Finally I ran the mktexlsr command from the ${TEXMF} folder, and this was enough to compile my paper.

So for those of you who like to copy paste, and assuming your tex folder structure is the same as mine (which it may not be), carry out the following commands (the first sudo command needs a password)

[FONT="Lucida Console"]cd /tmp
mkdir mathabx
wget [http://www-math.univ-poitiers.fr/~phan/downloads/metafont/mathabx.me.tar.gz](http://www-math.univ-poitiers.fr/~phan/downloads/metafont/mathabx.me.tar.gz)
tar xzvf mathabx.me.tar.gz
cd /usr/share/texmf-texlive/fonts/source/public
sudo mkdir mathabx
cd mathabx
sudo cp /tmp/mathabx/source/*.mf .
cd /usr/share/texmf-texlive/tex/latex
sudo mkdir mathabx
cd mathabx
sudo cp /tmp/mathabx/texinputs/mathabx.sty .
sudo cp /tmp/mathabx/texinputs/mathabx.dcl .
cd /usr/share/texmf-texlive/
sudo mktexlsr[/FONT]

Then simply go to your own tex files and try to compile, remember you need to include the line:
\usepackage{mathabx}

in your tex preamble.

I found mathabx to be useful for the $\bigcross$ symbol which I use to represent the cartesian product over n indexed sets. The library is large and useful though and I am sure I will dip into it again.

Happy tex-ing.

---

### Post by tqiw on 2008-03-28
In your example you don't 'cd' into /tmp/mathabx before extracting so in subsequent steps you need to remove 'mathabx' from any path starting with /tmp/mathabx.
Other than that the instructions worked perfectly for me. I use the package for the \divides and \notdivides binary operators.
Thanks.

---


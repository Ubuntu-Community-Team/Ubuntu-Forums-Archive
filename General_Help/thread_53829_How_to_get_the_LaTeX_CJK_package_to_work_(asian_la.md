---
title: "How to get the LaTeX CJK package to work? (asian language support)"
date: 2005-08-02
forum: General Help
---

### Post by kalle314 on 2005-08-02
I did install the cjk-latex package using Synaptic.

This was not enough, but i found [this page](http://www.physics.wustl.edu/~alford/tex/japanese_latex.html) which described how to install the cjk package.

Thus I downloaded the kanji48 directory.
The most important file (I think) is located here now:
/usr/local/share/texmf/fonts/hbf/jisx0208/kanji48/kanji48.hbf

Then I did what these instructions said - I wrote
MISCFONTS = .;$TEXMF/fonts/misc//;$TEXMF/fonts/hbf//
in the /usr/share/texmf/web2c/texmf.cnf file, and updated the database with
$ mktexlsr , but latex still would print out lots of errors when I gave it the example file found at that page as input.

After I did 
$ sudo apt-get install latex-ucs latex-ucs-uninames
to be able to write in swedish, latex would run the file without complaints, but now I get errors when I try to view the example file (with "xdvi japanese_template") - 
I get "Couldn't find `kanji48.hbf'", so maybe I have to write in the path to kanji48 at some other place too.

Also, ghostscript cannot read the example file
/usr/share/doc/gs-esp/examples/cjk/gscjk_aj.ps
(Error in findfont: Ryumin-Light-RKSJ-V).

---

### Post by kalle314 on 2005-08-03
The solution was simple - everything works if you stand at the root when you do 
$ mktexlsr

Next problem: How to write input files&#65311;

I have some problem making a correct input file using the uim-anthy input method (described in  [https://wiki.ubuntu.com//JapaneseInputHowto](https://wiki.ubuntu.com//JapaneseInputHowto) ).

If I try to write something in the template file, gedit wont let me save the document, because of "illegal byte sequence in conversion data".

Does anyone have a good template for CJK?

edit: Here is the problem -
Having followed [https://wiki.ubuntu.com//JapaneseInputHowto](https://wiki.ubuntu.com//JapaneseInputHowto) I have support for typing in japanese UTF-8, and I can do that in gedit but not emacs.
The example files
[http://www.ling.ed.ac.uk/~s0453746/japanese/first-night.tex](http://www.ling.ed.ac.uk/~s0453746/japanese/first-night.tex)
[http://www.physics.wustl.edu/~alford/tex/japanese_template.cjk](http://www.physics.wustl.edu/~alford/tex/japanese_template.cjk)
are in JIS format, which can not even be displayed correctly by gedit.

JIS format is what cjk needs for input, but according to [http://www.physics.wustl.edu/~alford/tex/japanese_latex.htm](http://www.physics.wustl.edu/~alford/tex/japanese_latex.htm) it should be possible to write a document.tex file in the format of your choice, and then create a document.cjk file in JIS format for the input to latex.

What is the most convenient way to do this? - Maybe I'll just try to follow the instructions in [http://www.physics.wustl.edu/~alford/tex/japanese_latex.html#emacs](http://www.physics.wustl.edu/~alford/tex/japanese_latex.html#emacs)

edit again: Wow - that worked, and all the necessary files was already there - thank you synaptic!

Next problem: How to write vertical text?

---


---
title: "Question regarding installation of TeX macros"
date: 2005-10-15
forum: General Help
---

### Post by concerned diagram user on 2005-10-15
Yes, hello. 

I'm trying to get a TeX package to work on my system and it's not going well. The package in question is [Paul Taylor's Commutative Diagrams]("http://www.cs.man.ac.uk/~pt/diagrams/"). Based on his instructions and those in [J.S. Milne's review]("http://www.jmilne.org/not/CDGuide.pdf"), I gather that I need to put the file [diagrams.tex]("http://www.cs.man.ac.uk/~pt/diagrams/diagrams.tex") in my "macros directory" and possibly change the name to diagrams.sty. 

The trouble is, being new to this, I'm not quite sure what directory I need to put the file in so that TeX or LaTeX will see it. There seem to be different conventions depending on the operating system and TeX distribution, but it looks like it should be some subdirectory of /usr/share/texmf. I've tried /usr/share/texmf/ and /usr/share/texmf/tex/latex/ without success.

As a test case, I've been trying to compile [the manual for the diagrams package]("http://www.cs.man.ac.uk/~pt/diagrams/ancient-manual.tex") given on Taylor's site. The results (only the last few lines seem to be relevant):

```
$ latex manual.tex

This is e-TeX, Version 3.14159-2.1 (Web2C 7.4.5)
entering extended mode
(./manual.tex
LaTeX2e <2001/06/01>
Babel <v3.7h> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, catalan, croatian, czech, danish, dutch, finnish, greek, iceland
ic, irish, italian, latin, magyar, norsk, norsk, portuges, romanian, russian, s
lovak, slovene, spanish, swedish, turkish, ukrainian, nohyphenation, loaded.
(/usr/share/texmf/tex/latex/base/latex209.def

          Entering LaTeX 2.09 COMPATIBILITY MODE
 *************************************************************
    !!WARNING!!    !!WARNING!!    !!WARNING!!    !!WARNING!!

 This mode attempts to provide an emulation of the LaTeX 2.09
 author environment so that OLD documents can be successfully
 processed. It should NOT be used for NEW documents!

 New documents should use Standard LaTeX conventions and start
 with the \documentclass command.

 Compatibility mode is UNLIKELY TO WORK with LaTeX 2.09 style
 files that change any internal macros, especially not with
 those that change the FONT SELECTION or OUTPUT ROUTINES.

 Therefore such style files MUST BE UPDATED to use
          Current Standard LaTeX: LaTeX2e.
 If you suspect that you may be using such a style file, which
 is probably very, very old by now, then you should attempt to
 get it updated by sending a copy of this error message to the
 author of that file.
 *************************************************************

(/usr/share/texmf/tex/latex/base/tracefnt.sty)
(/usr/share/texmf/tex/latex/base/latexsym.sty)
(/usr/share/texmf/tex/latex/config/latex209.cfg)
(/usr/share/texmf/tex/latex/tools/rawfonts.sty
(/usr/share/texmf/tex/latex/tools/somedefs.sty)
(/usr/share/texmf/tex/latex/base/ulasy.fd)))
(/usr/share/texmf/tex/latex/base/article.cls
Document Class: article 2001/04/21 v1.4e Standard LaTeX document class
(/usr/share/texmf/tex/latex/base/size10.clo))
Writing index file manual.idx
I can't find the commutative diagrams package, so I can't process the manual!
)

```

I doubt there's anything too mysterious here, I just can't seem to find the appropriate directory for this macro file. If there are any TeX users here, it's easy enough to reproduce my situation -- you only need the manual and macro files mentioned above. Any advice would be much appreciated.

---

### Post by Leif on 2005-10-15
here's how I did it :

sudo emacs /etc/texmf/texmf.d/05TeXMF.cnf
set : TEXMFLOCAL = whatever directory you want to use to store your local stuff
save & close
sudo update-texmf
sudo texhash

---

### Post by concerned diagram user on 2005-10-15
Hello, Leif, thank you for your prompt reply.

Having looked at the config file you mention, I see that it already has a local macro directory set, so I went ahead and put diagrams.sty in there. And I ran update-texmf (which I did not know about before) and texhash. I still get the same error, though.

I wonder if this is a package related issue. When you say "here's what I did" do you mean you did exactly that and managed to compile the manual with the diagram package I'm talking about or do you mean that that's your general procedure for adding new macros?

---

### Post by WW on 2005-10-15
If you rename the file to diagrams.sty, and put it in the same directory as manual.tex, it works.  I also latex'd a file containing the line \usepackage{diagrams}, and it compiled.  So just put diagrams.sty in the same directory as your latex files.  This is not a good solution for the long run, but it will work if you need to get something done quickly.

---

### Post by Leif on 2005-10-15
no, sorry, I didn't actually try to use the macros, what I wrote was simply what I do to tell tetex where my sty files are. have you tried putting the macro file in the same directory as the file you're trying to compile ? that should guarantee it's in the path.

---

### Post by concerned diagram user on 2005-10-15
Hm, I tried your same directory approach and it said the same thing again, so I downloaded both files over again and then it worked. Bizarre.

I'd like to get this thing working with LyX, but I guess I can just run LyX from the directory diagrams.sty is in and it should work the same way. Many thanks, WW and Leif.

---


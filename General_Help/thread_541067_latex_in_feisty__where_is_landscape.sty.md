---
title: "latex in feisty : where is landscape.sty ?"
date: 2007-09-02
forum: General Help
---

### Post by dusu on 2007-09-02
Hi

I recently upgraded to feisty (from breezy : yes I know, quite a leap forward !)
I want to write a LaTeX document in landscape format.
One should simply use the package landscape, but this does not work in feisty !

I tried :```
 locate landscape.sty
```
and this gives no location

then I tried :
```
sudo apt-file update
sudo apt-file search landscape.sty
```
and it tells me landscape.sty is provided in the package ptex-jtex
this was also true in breezy, though it was also provided in tetex-extra and tetex-src (which makes much more sense !)

I have already installed tetex-extra in feisty, but there is no landscape.sty file nowhere !

Could someone tell me what happened (in feisty or in between breezy and feisty) ?
I do not think ptex-jtex is needed, so I wonder whether there has been a problem somewhere ?

Thanks a lot for your help !

---

### Post by dusu on 2007-09-06
I can't believe no one out there is using LaTeX with Feisty :shock:

without joking, has someone a clue about this landscape problem ?

Thanks a lot !

---

### Post by iXce on 2007-09-07
Well, after looking around for a bit it appears that the file got lost in the change around dapper from tetex to texlive (texlive is supposed to be superior to tetex). The file isn't in current gutsy texlive source or upstream svn (well, I can't find it in my incomplete 2,8GB snapshot - my laptop's home got full'ed before the checkout finished).

I think you should file a bug on launchpad.net reporting a regression (your stuff was working before, it's not anymore). [This Launchpad page]("https://bugs.launchpad.net/ubuntu/+source/texlive-extra/") seems to be a good entry point for the report.

Good luck ;)

Edit : Oh and, well, it'd also be a lot more convenient and easier to just copy the file from tetex or from your breezy setup to your feisty until things get sorted upstream.

---

### Post by gaussian on 2007-09-07
There seem to be two issues: getting landscape.sty to work for you and filing a bug report on missing landscape.sty. For the first concern you could do the following (bit ugly, but won't mess up with anything):

1. Download landscape.sty  (not sure this is the latest version) from [http://tug.ctan.org/cgi-bin/getFile.py?fn=/macros/latex209/contrib/misc/landscape.sty](http://tug.ctan.org/cgi-bin/getFile.py?fn=/macros/latex209/contrib/misc/landscape.sty)

2. copy it to ~/texmf/tex/latex
You might have to create those directories

3. Run texhash using your regular user account

Caveat: I don't have my Ubuntu laptop with me now, this is how it would work in my Mandriva desktop that has TeTex. 

If and when the package gets updated to include landscape.sty you can just remove the manually copied version and re-run texhash.

---

### Post by dusu on 2007-09-08
Hi iXce and gaussian,

thanks a lot for the advices :)

I'll keep everyone informed using this thread

dusu

---

### Post by bns on 2007-09-08
For doing something in landscape, use:
```
\usepackage{lscape}
.
.
.
\begin{landscape}
.
.
.
\end{landscape}
```
I've never used "landscape.sty", but I suspect it's just an older implementation that has been replaced by "lscape.sty".  This happens alot with LaTeX.  Usually, the older package will hang around for a little while during the transition to the new package, but since you upgraded all the way from Breezy (!) you'll probably find that several packages have been replaced by others with a similar functionality.  I would be very surprised, however, if you actually lose any functionality.  Good luck, and feel free to ask if you have any other questions.

---

### Post by dusu on 2007-09-09
Hi

thanks a lot everyone for your answers.
Here is the status :
after reporting a bug on launchpad, I finally withdrew my bug report, since it seems landscape.sty was considered buggy and obsolete, and has been taken away.

I must admit it is quite strange for me that the tex people do not seem to care about compatibility with previous versions, so that older "code" can still be compiled with the newer distribution. :confused:

Anyway, I'll fix my problems in one of the two ways proposed in this thread...

Thanks again,
dusu

---


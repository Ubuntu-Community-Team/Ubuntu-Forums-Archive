---
title: "[SOLVED] Problem installing LaTex packages"
date: 2008-04-08
forum: General Help
---

### Post by Arrgoss on 2008-04-08
Hello,

I have recently witched to Ubuntu 7.10 AMD64 from windows. I used to use MikTex and Winedt, and now I want to use Kile instead.

I installed Kile and tried to compile some LaTex documents, but of course I need to install some packages. Though I'm not really sure how I should proceed in Ubuntu, I just went to synaptics and looked for some packages I need (texlive publishers, for example), but something goes wrong with the installation. I get the following message:
> 
E: tetex-base: subprocess post-installation script returned error exit status 127
E: texlive-fonts-recommended: subprocess post-installation script returned error exit status 127
E: texlive-latex-recommended: subprocess post-installation script returned error exit status 127
E: texlive: dependency problems - leaving unconfigured
E: tetex-bin: dependency problems - leaving unconfigured
E: revtex: dependency problems - leaving unconfigured
E: texlive-bibtex-extra: subprocess post-installation script returned error exit status 127
E: texlive-doc-en: subprocess post-installation script returned error exit status 127
E: texlive-font-utils: subprocess post-installation script returned error exit status 127
E: texlive-fonts-extra: subprocess post-installation script returned error exit status 127
E: texlive-lang-dutch: subprocess post-installation script returned error exit status 127
E: texlive-lang-french: subprocess post-installation script returned error exit status 127
E: texlive-lang-spanish: subprocess post-installation script returned error exit status 127
E: texlive-math-extra: dependency problems - leaving unconfigured
E: texlive-science: subprocess post-installation script returned error exit status 127
E: texlive-publishers: subprocess post-installation script returned error exit status 127

Is there anything I'm doing wrong? Any help is welcome. Easy on me, I'm new in Linux.

---

### Post by dvase on 2008-04-08
I wouldn't install any of tetex packages as it is no longer supported.  Its original maintainer suggests using texlive.  I have a functional latex installation, using only the texlive repository packages.

Additionally, if you are not opposed to compiling software, you can still use the command line version of miktex package manger (ie. no gui).  It is available here: [http://miktex.org/unx/](http://miktex.org/unx/)

---

### Post by Arrgoss on 2008-04-08
I didn't try to install tetex deliberately: I'd be happy with livetex. But now, every time I try to insta/uninstall anything (even not related to latex), I get the error message I copied above :confused:. What can I do to erase any tetex file and have a fresh and clean installation of livetex?

---

### Post by dvase on 2008-04-08
I found this in the Synaptic package manager help files, under "Known bugs and limitations"
> 

A failed installation blocks further operations in synaptic:

Under some rare circumstances the actual installation or removal of a package can fail.
As a consequence all other marked changes are canceled, too.

Synaptic Package Manager requires a
clear environment with no half installed packages
to perform additional changes. But at the moment there is no way to continue
canceled installations within Synaptic Package Manager.

To fix this situation type the following command in a terminal, then press
Return:

apt-get install -f


The issue sounds similar to yours.

---

### Post by Arrgoss on 2008-04-08
This is the answer:
```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

And I am administrator. In fact I'm the only one using this computer and I installed Ubuntu myself... I don't know what to do, or how to check whether I'm login as root.

---

### Post by YoG%*@ on 2008-04-08
> **Arrgoss said:**
> This is the answer:
```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```And I am administrator. In fact I'm the only one using this computer and I installed Ubuntu myself... I don't know what to do, or how to check whether I'm login as root.


you'd have to use sudo with the command: 
```

sudo apt-get install -f 

```

hth,
mux

(more info on sudo/root: [https://help.ubuntu.com/community/RootSudo)]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Arrgoss on 2008-04-08
I'm so sorry, I forgot the sudo and I panicked...

I used the command and this is what I got:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tetex-base (2007-10) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing tetex-base (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-fonts-recommended (2007-10) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-fonts-recommended (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-latex-recommended (2007-10) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-latex-recommended (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-7); however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on texlive (>= 2007-7); however:
  Package texlive is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of revtex:
 revtex depends on tetex-base; however:
  Package tetex-base is not configured yet.
 revtex depends on tetex-bin; however:
  Package tetex-bin is not configured yet.
dpkg: error processing revtex (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-bibtex-extra (2007-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-bibtex-extra (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-doc-en (2007-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-doc-en (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-font-utils (2007-12ubuntu3.1) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-font-utils (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-fonts-extra (2007-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-fonts-extra (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-lang-dutch (2007.dfsg.1-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-lang-dutch (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-lang-french (2007.dfsg.1-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-lang-french (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-lang-spanish (2007.dfsg.1-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-lang-spanish (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-publishers (2007-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-publishers (--configure):
 subprocess post-installation script returned error exit status 127
Setting up texlive-science (2007-3) ...
/usr/sbin/update-updmap: 427: getopt: not found
dpkg: error processing texlive-science (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 tetex-base
 texlive-fonts-recommended
 texlive-latex-recommended
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And the problem persists :(.

---

### Post by dvase on 2008-04-08
If I'm reading the error output correctly, it appears that you are missing the command "getopt".  This command is in the package "util-linux".  I would try reinstalling it if it is not already installed.

---

### Post by Arrgoss on 2008-04-08
> **dvase said:**
> If I'm reading the error output correctly, it appears that you are missing the command "getopt".  This command is in the package "util-linux".  I would try reinstalling it if it is not already installed.

That worked, thanks! The error message disappeared, and I uninstalled tetex and reinstalled texlive. I still cannot compile my tex files, though. Now, I'm apparently missing a sty file:
```
./testtest.tex:5:File `ams.sty' not found. \usepackage
```
Any advice on how to install this properly? Is there a way to get the missing packages on-the-fly, like with MikTex?

---

### Post by dvase on 2008-04-08
Glad to hear it worked.

> **Arrgoss said:**
> 
Any advice on how to install this properly? Is there a way to get the missing packages on-the-fly, like with MikTex?

I use the command line version of miktex to install packages, unfortunately it does not install on the fly as in windows.  Otherwise, the ams.sty package should be found in one of the texlive packages,  "texlive-math-extra" I think.

Package management seems to be one of the weaknesses of latex in *nix systems, which is part of the reason why I [pleged support to porting the miktex gui to Qt]("http://micropledge.com/projects/miktex-mpm-qt?do=pledge"), in hopes that it will spur further development of latex for *nix systems.

---

### Post by Arrgoss on 2008-04-08
I'm sorry I have to go now. I will be on day off-line, but I will get back to this post and let you know how it goes.
I will take a look to your pledge.

---

### Post by frisket on 2008-04-09
> **Arrgoss said:**
> That worked, thanks! The error message disappeared, and I uninstalled tetex and reinstalled texlive. I still cannot compile my tex files, though. Now, I'm apparently missing a sty file:
```
./testtest.tex:5:File `ams.sty' not found. \usepackage
```
Any advice on how to install this properly? Is there a way to get the missing packages on-the-fly, like with MikTex?

ams.sty has been obsolete for years. Use amsmath.sty instead, and amssymb.sty if you need the extra symbols.

///Peter

---

### Post by Arrgoss on 2008-04-10
> **frisket said:**
> ams.sty has been obsolete for years. Use amsmath.sty instead, and amssymb.sty if you need the extra symbols.


Thanks, I could compile it using amsmath!

I'd still like to ask you a couple of questions, regarding the use of latex and kile in Ubuntu. When I compile a document (a thesis with chapters, in different files), I get a message saying
> The document ____ is not a LaTeX root document; continue anyway?
I can continue and it goes through, but I could not find how to set up a root document, and what does that mean anyway.

I would like to be able to continue compiling, after getting some errors. I used to fo that in WinEdt by simple hitting "return", but I don't know how to continue with Kile, any idea?

Another problem is that, after LateX or PDFLateX compiling a file, and clicking to "viewDVI" or "viewPDF", the output file is not launched; I have to access to the folder and open it manually. Do you know how to fix that?

I really appreciate your help out there, guys.

---

### Post by dvase on 2008-04-10
> **Arrgoss said:**
> 
I'd still like to ask you a couple of questions, regarding the use of latex and kile in Ubuntu. When I compile a document (a thesis with chapters, in different files), I get a message saying

I can continue and it goes through, but I could not find how to set up a root document, and what does that mean anyway.
.
Creating a Kile project and defining a master document within the project should solve this issue.  Alternatively, you should be able to turn off this behavior by unchecking the appropriate option under the Latex Build Settings, found under Settings -> Configure Kile -> Tools -> Build -> Latex


> **Arrgoss said:**
> 
I would like to be able to continue compiling, after getting some errors. I used to fo that in WinEdt by simple hitting "return", but I don't know how to continue with Kile, any idea?
.
I'm not sure how to do this in Kile, I usually find it advantageous to deal with errors as soon as they appear.  That way they don't build up and turn into a unintelligible mess.

> **Arrgoss said:**
> 
Another problem is that, after LateX or PDFLateX compiling a file, and clicking to "viewDVI" or "viewPDF", the output file is not launched; I have to access to the folder and open it manually. Do you know how to fix that?
.
Check the settings in  Settings -> Configure Kile -> Tools -> Build for viewDVI and viewPDF.  Make sure that the programs being called (eg. kpdf) are installed.

---

### Post by Arrgoss on 2008-04-12
> **dvase said:**
> 
I'm not sure how to do this in Kile, I usually find it advantageous to deal with errors as soon as they appear.  That way they don't build up and turn into a unintelligible mess.
Yes, but sometimes is useful when I want to check some issues and, for example, a figure is not there.

> **dvase said:**
> 
Check the settings in  Settings -> Configure Kile -> Tools -> Build for viewDVI and viewPDF.  Make sure that the programs being called (eg. kpdf) are installed.
Since I'm using Gnome, I just changed the command from "kdvi" or "kpdf" to "evince". It works!

Now, strangely enough, it calls the "Bibliography" "Bibliographie" :confused:. Any idea why? Do you also know how to add a button (bibtex) to the toolbar?

EDIT: I answer myself to my last question. Settings --> Configure Toolbar.

---

### Post by dvase on 2008-04-12
> **Arrgoss said:**
> 
Now, strangely enough, it calls the "Bibliography" "Bibliographie" :confused:. Any idea why?


Where do you see this strange spelling? In the DVI/PDF file?

---

### Post by Arrgoss on 2008-04-12
> **dvase said:**
> Where do you see this strange spelling? In the DVI/PDF file?

Yes, in the PDF file. In both, the TOC and the text itself.

---

### Post by dvase on 2008-04-12
> **Arrgoss said:**
> Yes, in the PDF file. In both, the TOC and the text itself.

Curious, this sounds like an issue with a LaTeX setting.  I would double check the settings on the document class, bibliography style, and any included language packages.

---

### Post by Arrgoss on 2008-04-12
> **dvase said:**
> Curious, this sounds like an issue with a LaTeX setting.  I would double check the settings on the document class, bibliography style, and any included language packages.

It is indeed weird, since compiling in windows+winedt+miktex the output is "bibliography". My settings are the following:
```
\documentclass[a4paper,twoside,11pt,epsf]{mybook}
\usepackage[english,french,spanish,italian,dutch]{babel}
\bibliographystyle{prsty}
```

And in "mybook" the bibliography is defined as follows:
```
\newenvironment{thebibliography}[1]
     {\chapter*{\bfseries\sffamily\bibname
        \@mkboth{\sffamily\bibname}{\sffamily\bibname}}%
        \addcontentsline{toc}{chapter}{\bibname}%
        \small
      \list{\@biblabel{\@arabic\c@enumiv}}%
           {\settowidth\labelwidth{\@biblabel{#1}}%
            \leftmargin\labelwidth
            \advance\leftmargin\labelsep
            \itemsep\z@skip    % should this be commented out?
            \parsep\z@skip     % should this be commented out?
            \@openbib@code
            \usecounter{enumiv}%
            \let\p@enumiv\@empty
            \renewcommand\theenumiv{\@arabic\c@enumiv}}%
      \sloppy
      \clubpenalty4000
      \@clubpenalty \clubpenalty
      \widowpenalty4000%
      \sfcode`\.\@m}
     {\def\@noitemerr
       {\@latex@warning{Empty `thebibliography' environment}}%
      \endlist}
\newcommand\newblock{\hskip .11em\@plus.33em\@minus.07em}
\let\@openbib@code\@empty
```

And, lower:
```
\newcommand\bibname{Bibliography}
```

If I change that name, the output is still "Bibliographie". That's really unusual...

---

### Post by dvase on 2008-04-12
> **Arrgoss said:**
> 
If I change that name, the output is still "Bibliographie". That's really unusual...

I believe "Bibliographie" is the French word for Bibliography, thus my guess is that the French language package is redefining the value of \bibname

A quick and dirty hack that may work is to declare within your document right before the bibliography::
```

\renewcommand{\bibname}{Bibliography}

```

---

### Post by Arrgoss on 2008-04-12
> **dvase said:**
> I believe "Bibliographie" is the French word for Bibliography, thus my guess is that the French language package is redefining the value of \bibname

A quick and dirty hack that may work is to declare within your document right before the bibliography::
```

\renewcommand{\bibname}{Bibliography}

```

That worked, thanks!
Actually, bibliographie is the French for bibliography, and I'm indeed in France, but my computer and the programs installed are in English... Anyway, it's OK now. Thanks again.

---


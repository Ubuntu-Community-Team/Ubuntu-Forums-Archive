---
title: "problem with apt-get  texlive"
date: 2017-05-29
forum: General Help
---

### Post by wuhao-sife on 2017-05-29
hello everyone, 

I got problem with apt-get, right now it gives every time the same error after I fail to install some package from texlive(which I can't remember). So this is the error message, and the suggestion "apt-get -f install " doesn't make a difference. If anyone can help, I will appreciate it. 

Thanks in Advance 
Hao

```
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cm-super : Depends: tex-common (>= 3) but it is not going to be installed
 cm-super-minimal : Depends: tex-common (>= 3) but it is not going to be installed
 context : Depends: texlive-binaries (>= 2016)
           Depends: texlive-base (>= 2016) but 2013.20140215-1 is to be installed
           Depends: texlive-metapost (>= 2016) but 2013.20140215-1 is to be installed
           Depends: tex-common (>= 6) but it is not going to be installed
           Recommends: fonts-freefont but it is not installable
 context-modules : Depends: tex-common (>= 3) but it is not going to be installed
 dvipng : Depends: texlive-base-bin
 feynmf : Depends: tex-common (>= 3) but it is not going to be installed
          Depends: texlive-latex-base but it is not going to be installed
          Depends: texlive-font-utils but it is not going to be installed
          Depends: texlive-extra-utils but it is not going to be installed
 fonts-lmodern : Depends: tex-common (>= 4) but it is not going to be installed
 fonts-texgyre : Depends: tex-common (>= 4) but it is not going to be installed
 fragmaster : Depends: texlive-base-bin
              Depends: texlive-latex-base but it is not going to be installed
              Depends: texlive-extra-utils but it is not going to be installed
              Depends: texlive-font-utils but it is not going to be installed
 ko.tex-extra-hlfont : Depends: tex-common but it is not going to be installed
 latex-beamer : Depends: tex-common (>= 4) but it is not going to be installed
                Depends: texlive-latex-base but it is not going to be installed
 latex-cjk-chinese : Depends: tex-common (>= 3) but it is not going to be installed
 latex-cjk-chinese-arphic-bkai00mp : Depends: tex-common (>= 3) but it is not going to be installed
 latex-cjk-chinese-arphic-bsmi00lp : Depends: tex-common (>= 3) but it is not going to be installed
 latex-cjk-chinese-arphic-gbsn00lp : Depends: tex-common (>= 3) but it is not going to be installed
 latex-cjk-chinese-arphic-gkai00mp : Depends: tex-common (>= 3) but it is not going to be installed
 latex-cjk-common : Depends: texlive-latex-base but it is not going to be installed
                    Depends: texlive-font-utils (>= 2007.dfsg.2-1) but it is not going to be installed
                    Depends: tex-common (>= 4) but it is not going to be installed
 latex-cjk-japanese : Depends: tex-common (>= 4) but it is not going to be installed
 latex-cjk-japanese-wadalab : Depends: tex-common (>= 3) but it is not going to be installed
 latex-cjk-korean : Depends: tex-common (>= 4) but it is not going to be installed
 latex-cjk-thai : Depends: texlive-latex-base but it is not going to be installed
                  Depends: tex-common (>= 4) but it is not going to be installed
                  Depends: texlive-lang-other (>= 2013.20130523-1) but it is not going to be installed
 latex-sanskrit : Depends: tex-common (>= 3) but it is not going to be installed
 latex-xcolor : Depends: tex-common (>= 3) but it is not going to be installed
 latexmk : Depends: texlive-latex-base but it is not going to be installed
 lmodern : Depends: tex-common (>= 3) but it is not going to be installed
 pgf : Depends: tex-common (>= 2.00) but it is not going to be installed
 preview-latex-style : Depends: tex-common (>= 3) but it is not going to be installed
 prosper : Depends: texlive-latex-base but it is not going to be installed
           Depends: tex-common (>= 1.10) but it is not going to be installed
 tex-gyre : Depends: tex-common (>= 3) but it is not going to be installed
 tex4ht : Depends: texlive-base-bin
 tex4ht-common : Depends: texlive-base-bin
 texlive-base : Depends: tex-common (>= 4.03) but it is not going to be installed
                Depends: luatex (>= 0.70.1)
                Depends: texlive-binaries (>= 2013.20130512)
 texlive-fonts-extra-doc : Depends: texlive-base (>= 2016) but 2013.20140215-1 is to be installed
                           Depends: tex-common (>= 6) but it is not going to be installed
 texlive-fonts-recommended-doc : Depends: texlive-base (>= 2016) but 2013.20140215-1 is to be installed
                                 Depends: tex-common (>= 6) but it is not going to be installed
 texlive-full : Depends: texlive-lang-japanese (>= 2016) but it is not going to be installed
                Depends: texlive-latex-base-doc (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-games (>= 2016) but it is not going to be installed
                Depends: texlive-publishers-doc (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-lang-german (>= 2016) but it is not going to be installed
                Depends: texlive-lang-polish (>= 2016) but it is not going to be installed
                Depends: texlive-math-extra (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-omega (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-lang-english (>= 2016) but it is not going to be installed
                Depends: texlive-lang-other (>= 2016) but it is not going to be installed
                Depends: texlive-htmlxml (>= 2016) but it is not going to be installed
                Depends: texlive-lang-cjk (>= 2016) but it is not going to be installed
                Depends: texlive-bibtex-extra (>= 2016) but it is not going to be installed
                Depends: texlive-pictures-doc (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-lang-greek (>= 2016) but it is not going to be installed
                Depends: texlive-base (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-latex-extra-doc (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-lang-chinese (>= 2016) but it is not going to be installed
                Depends: texlive-pstricks (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-font-utils (>= 2016) but it is not going to be installed
                Depends: texlive-music (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-binaries (>= 2016.20160409.40358-1)
                Depends: texlive-latex-base (>= 2016) but it is not going to be installed
                Depends: texlive-lang-czechslovak (>= 2016) but it is not going to be installed
                Depends: texlive-lang-arabic (>= 2016) but it is not going to be installed
                Depends: texlive-lang-italian (>= 2016) but it is not going to be installed
                Depends: texlive-lang-korean (>= 2016) but it is not going to be installed
                Depends: texlive-generic-extra (>= 2016) but it is not going to be installed
                Depends: texlive-fonts-recommended (>= 2016) but it is not going to be installed
                Depends: texlive-formats-extra (>= 2016) but it is not going to be installed
                Depends: texlive-science-doc (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-luatex (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-lang-spanish (>= 2016) but it is not going to be installed
                Depends: texlive-xetex (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-humanities (>= 2016) but it is not going to be installed
                Depends: texlive-latex-recommended-doc (>= 2016) but 2013.20140215-1 is to be installed
                Depends: prerex but it is not going to be installed
                Depends: texlive-plain-extra (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-pictures (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-latex-extra (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-generic-recommended (>= 2016) but it is not going to be installed
                Depends: texlive-lang-portuguese (>= 2016) but it is not going to be installed
                Depends: texlive-lang-african (>= 2016) but it is not going to be installed
                Depends: texlive-metapost-doc (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-fonts-extra (>= 2016) but it is not going to be installed
                Depends: texlive-extra-utils (>= 2016) but it is not going to be installed
                Depends: texlive-lang-european (>= 2016) but it is not going to be installed
                Depends: texlive-science (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-publishers (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-lang-indic (>= 2016) but it is not going to be installed
                Depends: texlive-pstricks-doc (>= 2016) but 2013.20140215-2 is to be installed
                Depends: texlive-metapost (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-lang-french (>= 2016) but it is not going to be installed
                Depends: texlive-latex-recommended (>= 2016) but 2013.20140215-1 is to be installed
                Depends: texlive-lang-cyrillic (>= 2016) but it is not going to be installed
 texlive-humanities-doc : Depends: tex-common (>= 6) but it is not going to be installed
                          Depends: texlive-base (>= 2016) but 2013.20140215-1 is to be installed
 texlive-latex-base-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-latex-extra : Depends: luatex
                       Depends: tex-common (>= 3) but it is not going to be installed
                       Depends: texlive-binaries (>= 2013.20130512)
 texlive-latex-extra-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-latex-recommended : Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
                             Depends: texlive-binaries (>= 2013.20130512)
                             Depends: tex-common (>= 3) but it is not going to be installed
 texlive-latex-recommended-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-luatex : Depends: texlive-binaries (>= 2013.20130512)
                  Depends: tex-common (>= 3) but it is not going to be installed
                  Depends: luatex (>= 0.70.1)
 texlive-math-extra : Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
                      Depends: texlive-fonts-recommended (>= 2013.20130512) but it is not going to be installed
                      Depends: texlive-binaries (>= 2013.20130512)
                      Depends: tex-common (>= 3) but it is not going to be installed
 texlive-metapost : Depends: texlive-binaries (>= 2013.20130512)
                    Depends: tex-common (>= 3) but it is not going to be installed
 texlive-metapost-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-music : Depends: musixtex (>= 1:0.114-2)
                 Depends: texlive-binaries (>= 2013.20130512)
                 Depends: m-tx
                 Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
                 Depends: tex-common (>= 3) but it is not going to be installed
                 Depends: luatex
                 Depends: pmx
 texlive-omega : Depends: texlive-binaries (>= 2013.20130512)
                 Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
                 Depends: tex-common (>= 3) but it is not going to be installed
 texlive-pictures : Depends: tex-common (>= 3) but it is not going to be installed
                    Depends: luatex
                    Depends: texlive-binaries (>= 2013.20130512)
 texlive-pictures-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-plain-extra : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-pstricks : Depends: texlive-generic-recommended (>= 2013.20130512) but it is not going to be installed
                    Depends: tex-common (>= 3) but it is not going to be installed
                    Depends: texlive-binaries (>= 2013.20130512)
                    Recommends: texlive-font-utils but it is not going to be installed
                    Recommends: texlive-extra-utils but it is not going to be installed
 texlive-pstricks-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-publishers : Depends: tex-common (>= 3) but it is not going to be installed
                      Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
 texlive-publishers-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-science : Depends: tex-common (>= 3) but it is not going to be installed
                   Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
                   Depends: texlive-binaries (>= 2013.20130512)
 texlive-science-doc : Depends: tex-common (>= 3) but it is not going to be installed
 texlive-xetex : Depends: texlive-latex-base (>= 2013.20130512) but it is not going to be installed
                 Depends: texlive-binaries (>= 2013.20130512)
                 Depends: tex-common (>= 3) but it is not going to be installed
 tipa : Depends: texlive-latex-base but it is not going to be installed
        Depends: texlive-base-bin
        Depends: tex-common (>= 3) but it is not going to be installed
```

---

### Post by ian-weisser on 2017-05-29
Looks like you are trying to mix different versions of texlive,
or in the past you tried (and failed) to install a version of texlive that was incompatible with your release of Ubuntu...and never cleaned it up,
or you are currently trying to install a version of texlive that is incompatible with your release of Ubuntu.

What release of Ubuntu are you running?
Did you previously try and fail to install texlive?
What instructions did you follow then? What instructions are you following now?
Detailed answers are better.

---

### Post by wuhao-sife on 2017-05-30
Hi I think you are right, I'm running ubuntu 14.04 LTS, I tried to install a CV template, [https://github.com/posquit0/Awesome-CV](https://github.com/posquit0/Awesome-CV), to compile it, I download some Font files, 
I don't really remember which, and I always use apt-get install. I tried to uninstall texlive, but also failed. The apt-get seems crash.  


Thanks 
Hao

---


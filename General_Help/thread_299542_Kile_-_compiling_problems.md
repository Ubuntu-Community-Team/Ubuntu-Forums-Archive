---
title: "Kile - compiling problems"
date: 2006-11-14
forum: General Help
---

### Post by ErrorAttractor on 2006-11-14
Hello, I'm a newbie and I'm having problems using Kile 1.9.2 in Ubuntu 6.10. 

Problem: 
 - When ever I try to compile tex-files to dvi-files I get following error message:

[LaTeX] example.tex => example.dvi (latex)
[LaTeX] finished with exit status 1
/usr/share/texmf-tetex/tex/latex/base/fontenc.sty:100:Font T1/cmr/m/n/10.95=ecrm1095 at 10.95pt not loadable: Metric (TFM) file notfound. \fontencoding\encodingdefault\selectfont
./example.tex:40:Font T1/cmr/m/n/14.4=ecrm1440 at 14.4pt not loadable: Metric (TFM) file not found. $
./example.tex:40:Font T1/cmr/bx/n/14.4=ecbx1440 at 14.4pt not loadable: Metric (TFM) file notfound. $
./example.tex:43:Command \textcurrency unavailable in encoding T1. \section
./example.tex:60:Command \textcurrency unavailable in encoding T1. \item{"example section")
[LaTeX] 5 errors, 0 warnings, 0 badboxes

Apparently some weird fonts (ecrm1440,ecbx1440,...) are missing :confused: . Does anyone have a solution to this problem?

---


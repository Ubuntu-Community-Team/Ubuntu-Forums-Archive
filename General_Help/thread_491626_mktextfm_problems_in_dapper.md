---
title: "mktextfm problems in dapper"
date: 2007-07-03
forum: General Help
---

### Post by trio123 on 2007-07-03
There seems to be a problem generating tfm fonts in dapper.

I get the following error when I try to latex a file as a non root user.

_______________________________________________________________________________________________
 (/usr/share/texmf-tetex/tex/latex/base/t1cmtt.fd)kpathsea: Running mktextfm eccc0800
mktextfm: Running mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input eccc0800
This is METAFONT, Version 2.71828 (Web2C 7.5.4)
(Fatal base file error; I'm stymied)
grep: eccc0800.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input eccc0800' failed to make eccc0800.tfm.
kpathsea: Appending font creation commands to missfont.log.

! Font T1/cmr/m/sc/8=eccc0800 at 8.0pt not loadable: Metric (TFM) file not foun
d.
<to be read again>
                   relax
l.250 \end{document}
____________________________________________________________________________________

To get around this I had to 
run 
mktextfm eccc0800.tfm
as root to generate the font.

My /var/cache/fonts directory and everything below it is writable by everyone.

Any idea?

Thanks in advance

---


---
title: "Please test this for me (very quick) ! pstools broken on Ubuntu 8.04"
date: 2008-05-11
forum: General Help
---

### Post by cpbl on 2008-05-11
Consider the simple PDF file, testgs.pdf, here: [http://launchpadlibrarian.net/13168232/testgs.pdf](http://launchpadlibrarian.net/13168232/testgs.pdf)

Trying the following simple use of ps / pdf tools:

```
pdftops testgs.pdf
mv testgs.ps testgs.pdf.ps
pstopdf testgs.pdf.ps

```

gives the following fatal error:

```

PsToPdf | converting ps (ps) into pdf
PsToPdf | conversion method 2
PsToPdf | converting testgs.pdf.ps bounded
```

Error: /undefined in Aa!6FDeg#oPkTbgb
Operand stack:

Execution stack:
   %interp_exit .runexec2 --nostringval-- --nostringval-- --nostringval-- 2 %stopped_push --nostringval-- --nostringval-- --nostringval-- false 1 %stopped_push 1905 1 3 %oparray_pop 1904 1 3 %oparray_pop 1888 1 3 %oparray_pop 1771 1 3 %oparray_pop --nostringval-- %errorexec_pop .runexec2 --nostringval-- --nostringval-- --nostringval-- 2 %stopped_push --nostringval--
Dictionary stack:
   --dict:1152/1684(ro)(G)-- --dict:0/20(G)-- --dict:93/200(L)-- --dict:65/75(L)-- --dict:18/25(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 8.61: Unrecoverable error, exit code 1
PsToPdf | job aborted due to some error: Broken pipe
[/CODE]

Do you get this too? None of the standard ps manipulations on pdf files work for me since some update in Gutsy...
I want to know whether I have something local going on.

---

### Post by mannheim on 2008-05-11
There's no "pstopdf" on my system; but there is "ps2pdf" (which is installed as part of the ghostscript package). The following works without problem:

```
pdf2ps testgs.pdf
mv testgs.ps testgs.pdf.ps
ps2pdf testgs.pdf.ps
```

on Ubuntu 8.04.

---


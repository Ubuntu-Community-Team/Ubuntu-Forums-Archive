---
title: "kile+KDVI question"
date: 2008-02-24
forum: General Help
---

### Post by geo909 on 2008-02-24
Hello everybody!
I use Kile as my TeX editor and KDVI as the DVI viewer that works with it.
I use 'forward DVI' (that is, jump to the appropriate area of the DVI file when you write code) quite a lot and I have a related question:

I wonder if it is possible when I do 'forward DVI' to make KDVI go to the foreground (appear on the top of Kile). I know it's not so important but it would be *really* convenient for me...

If you know anything, please take the time to answer this.


   Thanks in advance!

---

### Post by geo909 on 2008-02-24
I know that I need a quite special advice.
So I will bump it up for a few days, sorry for that!

*BUMP*

---

### Post by geo909 on 2008-02-24
bump

---

### Post by geo909 on 2008-02-24
bump

---

### Post by Eothred on 2008-05-27
Huh? Wouldn't this be satisfied by the embedded version? I use this for quick-compile:
Latex(modern)
ForwardDVI(embedded viewer) <-- This should satisfy your need if I understand you correctly!
DVItoPDF(default)
Archive(tar+gzip)

Now for the dvitopdf I use dvipdf and not dvipdfm due to the fact that I had some problems not getting the links from the hyperref package I use. The real beauty is the Archive I think (maybe I think so because I just realised it was possible to do). I added the following option " zcvf ../Backup/'%S'_`date +'%Y-%m-%d'`.tar.gz %AFL "
What this gives me is a separate folder with a backup from each day I have been working on the project from each project, sorted by date. For the type of use I have, this is nothing short of extremely practical. Recommended! The forward search and reverse search in dvi is also something I haven't been using before (I was used to the old habit of pdflatex and kpdf). Now I can't live without it!:)

---


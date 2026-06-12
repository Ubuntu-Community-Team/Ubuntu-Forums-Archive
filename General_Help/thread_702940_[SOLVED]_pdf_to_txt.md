---
title: "[SOLVED] pdf to txt?"
date: 2008-02-20
forum: General Help
---

### Post by querent on 2008-02-20
Any way to convert a pdf to txt?  anybody know?  found a windows application.  i know i'll lose graphics and what not.  that's fine.  i wanna read math books on my new iriver.

---

### Post by querent on 2008-02-20
oh...thanks all!

---

### Post by astrotech226 on 2008-02-20
This works pretty good for me:

```
sudo apt-get install pstotext
```

You can then run it directly on postscript or pdf files.  Postscript can be from stdin, pdf must be from a file.

```
pstotext example.pdf
```

---

### Post by harold4 on 2008-02-20
kword can also do this.

---

### Post by querent on 2008-02-22
couldn't figure out where pstotext actually put the file.  maybe i'm being dumb, who knows.  (maybe somebody.)  trying kword now.

thanks all!

---

### Post by HermanAB on 2008-02-22
$ pdf2[tab]
pdf2dsc  pdf2ps

$ ps2[tab]
ps2ascii        ps2lexmark      ps2pdf12        ps2pdfwr
ps2epl.pl       ps2lwxl         ps2pdf13        ps2pk
ps2epsi         ps2monolexmark  ps2pdf14        ps2ps
ps2frag         ps2pdf          ps2pdfpress     ps2ps2

---

### Post by Priit Tamboom on 2008-07-01
@astrotech226: tanks for the tip

@querent: pipe output to example.txt file like this:
```

pstotext example.pdf > example.txt
```

---

### Post by querent on 2008-07-15
Hey, thanks.

thanks to Priit Tamboom

---


---
title: "&quot;cannot convert string&quot; while using gv"
date: 2013-11-18
forum: General Help
---

### Post by manurecondo on 2013-11-18
hi, i recently installed GMT (Generic Mapping Tool) which allows the user to create maps in the format "file.ps". after a few instructions i tried to open my created file (mapa.ps) using GhostScript. Here is the result: 

gv mapa.ps
Warning: Cannot convert string "-*-Helvetica-Medium-R-Normal--*-140-*-*-P-*-ISO8859-1" to type FontStruct
Warning: Cannot convert string "-*-Helvetica-Medium-R-Normal--*-120-*-*-P-*-ISO8859-1" to type FontStruct
Warning: Cannot convert string "-*-Helvetica-Medium-R-Normal--*-100-*-*-P-*-ISO8859-1" to type FontStruct
gv: Cannot open file mapa.ps (No data available)

Any suggestions?

---

### Post by Impavidus on 2013-11-19
Never heard or type fontstruct. Postscript uses the dictionary type for fonts. Could be something internal in gv...

Anyway, it seems it cannot find the required fonts. These are only warnings and shouldn't cause a crash, as gv should automatically substitute something different, or an empty font producing no text at all. The required fonts are Helvetica Roman in the ISO 8859-1 encoding, optimised for three specific sizes.

You could try and find the fonts somewhere and properly installing them (I've got no idea how), try a different program that nicely manages to substitute something (try converting to pdf). I won't advise you to hack your way into the file and substitute something manually...

---

### Post by steeldriver on 2013-11-19
It probably just means that the file you created with GMT is empty - e.g. if I create an empty file

```
$ touch mapa.ps
```
then
```

$ gv mapa.ps
Warning: Cannot convert string "-*-Helvetica-Medium-R-Normal--*-140-*-*-P-*-ISO8859-1" to type FontStruct
Warning: Cannot convert string "-*-Helvetica-Medium-R-Normal--*-120-*-*-P-*-ISO8859-1" to type FontStruct
Warning: Cannot convert string "-*-Helvetica-Medium-R-Normal--*-100-*-*-P-*-ISO8859-1" to type FontStruct
gv: Cannot open file mapa.ps **(No data available)**

```

whereas if I use a known good ps file it works
```

$ gv tri.ps

```

What does 

```

$ ls -l mapa.ps

```

say about the file size?

---

### Post by manurecondo on 2013-11-20
thank u guys for answering, i realized that mapa.ps was an empty file, but the problem still occurs with a known good ps file, so its probably a gv problem. do u know another good program to view ps files??

---

### Post by Impavidus on 2013-11-20
evince (the default pdf viewer) usually does a decent job, as do most pdf viewers. Most support ps too.

---


---
title: "LaTeX \bf{} command makes all document bold"
date: 2004-12-05
forum: General Help
---

### Post by karih on 2004-12-05
Ok, this is really strange.  I have a .tex file with the following text
```

...
\begin{document}
\maketitle

\section{Bókmenntir á lærdómsöld}
Tímabilið 1550 - 1800 kallast \bf{lærdómsöld}.  Á því tímabili gætti áhrifa frá endurreisn og fornmenntastefnu eða húmanisma (upptök á Ítalíu 1400).  Kom þessa stefna fram í áhuga á menningu, sögu, klassískum bókmenntum og fræðimennsku.  Tekið var það mannlega fram yfir hið guðlega.
Þetta varð undirrótin að uppreisn klerka sem leiddi af sér Lútherstrú (hófst með Marteini Lúther).  Dýrlingar voru afnumdir og syndaaflausn fékkst ekki keypt.
...
```But just after the first \bf{} the rest of the document becomes bold.  I once had the same problem with \em but fixed that with adding another \em after it (very bad but worked).
Is there something I am missing here?

Thanks in advance!

---

### Post by WW on 2004-12-05
In latex, \bf does not have an argument.  Either do this:```
... kallast {\bf lærdómsöld}.  Á því ...
```or use **\textbf**:```
... kallast \textbf{lærdómsöld}.  Á því ...
```

---

### Post by karih on 2004-12-05
Okay, thanks!

---


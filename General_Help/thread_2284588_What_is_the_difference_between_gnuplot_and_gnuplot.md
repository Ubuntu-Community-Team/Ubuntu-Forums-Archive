---
title: "What is the difference between gnuplot and gnuplot-x11?"
date: 2015-06-30
forum: General Help
---

### Post by arroy_0209 on 2015-06-30
I am using lubuntu and need to install gnuplot. However I notice there are two different packages available: gnuplot and gnuplot-x11. What is the difference between these two? How do I decide which one will be more suitable for my purpose? (I plan to install using the apt-get command.)

---

### Post by steeldriver on 2015-06-30
IIRC plain gnuplot only gives file-based output (i.e. plotting directly to .png, .pdf etc.) whereas gnuplot-x11 includes support for rendering plots to screen using the default wxt term type, xlib etc.

---

### Post by tgalati4 on 2015-06-30
There's even a QT front-end for gnuplot.

```
apt-cache search gnuplot
```

---


---
title: "gnuplot copy/paste doesn't work"
date: 2013-09-08
forum: General Help
---

### Post by Zahc on 2013-09-08
I am using gnuplot 4.4.3 on ubuntu 12.04 lts. Everything works except for the copy and paste feature. Does anyone know how I can save my plot into an image file that I can then insert into a word document?
Thanks

---

### Post by steeldriver on 2013-09-08
You can plot directly to a PNG/EPS/whatever file by setting the 'term' (or 'terminal') value e.g.

```

gnuplot> set term png
gnuplot> set output 'data1.png'
gnuplot> plot 'data1.dat' with linespoints

```

For a complete list of available terminal types available on your system, use 'set term' without arguments

```
gnuplot> set term
```

---

### Post by Zahc on 2013-09-08
Thanks, it worked.

---


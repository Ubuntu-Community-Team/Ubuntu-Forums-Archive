---
title: "gnuplot not showing any plots"
date: 2007-11-24
forum: General Help
---

### Post by Tunguska on 2007-11-24
Hello,

I installed gnuplot yesterday, following the instruction in the INSTALL file. Everything went fine, but when I try to plot any kind of function, it just goes to the next command line. It doesn't give any errors, but it's not opening a new window with the plot either. Any help would be appreciated.

---

### Post by luisfcup on 2007-11-25
What is the terminal you are using?
The terminal set should appear right above the "gnuplot>" line when you start gnuplot.
Try setting the terminal to x11:
```
gnuplot> set terminal x11
```
If you have x11 terminal installed this should give you the plot in a separate window.

---


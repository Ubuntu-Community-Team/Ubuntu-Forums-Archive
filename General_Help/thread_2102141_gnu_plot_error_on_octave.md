---
title: "gnu plot error on octave"
date: 2013-01-06
forum: General Help
---

### Post by fr33c0untry on 2013-01-06
hi,
i have octave installed on ubuntu 12.04 a month ago from the software center.it has been working fine until today when i tried to plot a function and an error showed up.i tried loading some .m files which involved plotting but failed because of the same error.the error i get is:
<raw>
error: invalid use of script in index expression
error: called from:
error:   /usr/share/octave/3.2.4/m/strings/strsplit.m at line 49, column 13
error: evaluating argument list element number 1
error: evaluating argument list element number 1
error: evaluating argument list element number 1
error: evaluating argument list element number 1
error:   /usr/share/octave/3.2.4/m/miscellaneous/compare_versions.m at line 112, column 7
error:   /usr/share/octave/3.2.4/m/plot/__gnuplot_has_feature__.m at line 43, column 23
error:   /usr/share/octave/3.2.4/m/plot/gnuplot_drawnow.m at line 229, column 11
error:   /usr/share/octave/3.2.4/m/plot/gnuplot_drawnow.m at line 97, column 16
</raw>
i dont know what to fix as it seems that there is some error with the source code(correct me if im wrong).i tried to uninstall gnuplot from software center and then reinstall it but that didn't work either.
looking forward to a reply 
thanks

---

### Post by userdce on 2013-01-06
Atleast it could be helpful if you had pasted the .m code

---

### Post by fr33c0untry on 2013-01-07
that doesn't matter,i tried it for several other .m files which used the plot function and it worked fine before this error started to show up.i always get the same error regardless of what i plot.

---

### Post by steeldriver on 2013-01-07
I think that happens when your local .m file name is conflicting with a library .m file name e.g.

```
$ cat myplot.m
x=1:10;
plot(x);

``````
octave:3> myplot
octave:4>
```works fine; but
```
$ mv myplot.m plot.m
``````
octave:4> plot
error: invalid use of script in index expression
error: called from:
error:   /home/steeldriver/test/plot.m at line 3, column 1
```

---


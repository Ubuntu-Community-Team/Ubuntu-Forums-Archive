---
title: "scientific graph software"
date: 2008-01-24
forum: General Help
---

### Post by Xbehave on 2008-01-24
Im doing my 2nd year at uni and the chemistry department dont allow me to use excel to make graphs as their to simple so i have to do them by hand.

what is the best OSS graph plotting software that will suit my needs:
NEEDS: be able to plot errors bars (custom heights based on the data i give it)
GOOD: be able to plot 3 lines of best fit based on error bars
GREAT: be able to pick anomalous point and have them ignored

also useful but unneeded would be the ability to do my data manipulation in the software.

also important is that i can use it without spending agers learning it. ( im used to spreadsheets and have used a few data plotting suits )

p.s if this is not in the right forum feal free to move it

---

### Post by Rhubarb on 2008-01-24
Try OpenOffice.org's Spreadsheet.
There are other graphing applications that are available in the repositories, but I'm not sure they'd be suitable for your application.

---

### Post by Xbehave on 2008-01-27
OpenOffice isnt suitible it cant do custom error bars and certainly cant do any of the other points.
gnumeric can do custom error bars but it cant do any of the rest.

---

### Post by heindsight on 2008-01-27
I usually use gnuplot for all my plotting needs. I'm not sure it does everything you want, but it's worth taking a look at.

It definitely can do error bars.
It can do least squares curve fitting, I'm not sure about fitting the 3 best lines, but it might be possible.
It is possible to use only a subset of the data for plotting or fitting, I'm not sure it's exactly what you want though (I don't use that functionality very often).

It does take a bit of time to learn to use gnuplot, but the documentation and online help files are quite good. gnuplot is command-line oriented, but there are GUIs available too (I've never used any of the GUIs, so I don't know how good they are.)

---

### Post by amo-ej1 on 2008-01-27
Indeed, gnuplot is the de facto standard plotting software in the unix world. You can either use gnuplot directly or you could take a look at gnu octave, which is an open source matlab clone, this also uses gnuplot as a plotting backend, however it provides you with a whole set of mathematical function.

Both tools are text-based and will require some reading in order to learn to work with them .

---


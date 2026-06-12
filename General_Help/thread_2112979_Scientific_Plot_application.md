---
title: "Scientific Plot application"
date: 2013-02-06
forum: General Help
---

### Post by ACon125 on 2013-02-06
Hi everybody, 
I wonder if someone can suggest me a good application for data analysis, statistic and 2Dplot. 
I'm using Xubuntu 12.04
If it has a beginner friendly installation even better
Thanks in advance

---

### Post by Impavidus on 2013-02-06
Most scientists I know (astrophysicists) use either gnuplot (as an application) or pgplot (as a library, you have to write your own C or fortran code to use it) for plotting. As for analysis, are you dealing with dozens of data points or millions of data points? For small data sets any spreadsheet program can probably do the job, for big ones you can better write your own code. Python could also be useful.

---

### Post by SeijiSensei on 2013-02-06
I don't know what kind of statistics you are doing, but I'll suggest [gretl]("http://gretl.sourceforge.net/"), the GNU econometrics package.  It has good facilities for importing and exporting data from standard formats including CSV and ODF and a simple interface to gnuplot.  It opens with a GUI but also contains an optional command window where you can create plots just by typing simple commands. 

There is also a GNU-sponsored clone of SPSS called [PSPP]("http://www.gnu.org/software/pspp/").  I haven't tried graphing with that.  I use it mostly to generate frequencies and crosstabs from survey data.

Both gretl and pspp are in the Ubuntu repositories.  

However for most graphing I use LibreOffice Calc.  It has some annoying quirks, but it produces nicely styled charts.  Gnumeric uses gnuplot, and the graphs are not as visually appealing.  If you intend to include them in a document or blog post, I'd go with Calc.

Here's a [plot from Gnumeric](http://www.politicsbythenumbers.org/wp-content/uploads/2012/11/variability5.png), and here's a similar [plot from Calc]("http://www.politicsbythenumbers.org/wp-content/uploads/2012/11/votes-seats-by-year.png").

---

### Post by ACon125 on 2013-02-06
I'll try to find a bit of documentation about the programs you recommended.
For clarity, I'm after an application able to plot data, do some statistics and calculate parameters for linear (and non-linear) fit. 
Thanks guys for your kind ( and quick) response.

---

### Post by steeldriver on 2013-02-06
There's also 'octave' - it has pretty much the same linear least squares fitting capabilities as MATLAB - nonlinear minimization is a bit more spotty but I've had good results with octave's 'sqp'

---

### Post by SeijiSensei on 2013-02-06
> **ACon125 said:**
> For clarity, I'm after an application able to plot data, do some statistics and calculate parameters for linear (and non-linear) fit. 

Gretl does all forms of least squares, including nonlinear least squares, as well as the full array of common maximum-likelihood estimates like probit and logit.  It's really quite impressive and definitely worth your attention.

---

### Post by ACon125 on 2013-02-09
I settled it for gretl + gnuplot.
It does the job for me.
recommended

---

### Post by frncz on 2013-02-09
Do try gnumeric. It's great for graphs

---


---
title: "Librecalc Curve Fitting"
date: 2014-06-05
forum: General Help
---

### Post by mark bower on 2014-06-05
librecalc draws a nice logrithmic line through my x-y plotted data.  is there a way to get the formula that librecalc must have calculated in order to draw the smooth curve?  if not, please recommend a simple software that will do this.

in fact, i am trying to determine the IRS formula used to determine the Required Minimum Distribution(RMD) versus age found in IRS Pub 590, Appendix C, Table III.  it starts at 27.4 for age 70, and drops to 10.2 at age 92, but it is not a linear drop per year.

mark bower

---

### Post by steeldriver on 2014-06-05
If you plot your chart as a scatter plot of points (without the automatic line), then select the series and "Insert --> Trend lines... " you should be able to select a logarithmic trend line explicitly, and there should be a checkbox for 'Show Equation' in the dialog box

---

### Post by mark bower on 2014-06-05
wow, thank you ever so much.  yes, Insert>Trendlines>Logrithmic and a **check mark in "Show Equation"** does the trick.  i have spent the last 4 hours trying to match the data with formulae, but did not get close enough for my satisfaction.  sorry i did not see your post sooner!  this is an exercise to evaluate the merits of converting retirement accounts to a Roth IRA to help combat taxes down the road.

mark bower

---


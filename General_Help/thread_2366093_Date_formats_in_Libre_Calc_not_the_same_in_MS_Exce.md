---
title: "Date formats in Libre Calc not the same in MS Excel"
date: 2017-07-14
forum: General Help
---

### Post by richlyn9 on 2017-07-14
Hi All,

I am not sure if this is the right place for  a question on Libre off calc date formats, but hoping i get some guidance.
Here goes...
When i work on libre off calc in ubuntu the date formats seen are as desired.
however the same breaks when opened in ms excel in windows.

in excel its is seen as custom/ text/ general format and hence any calculation done on that cell is not matching with that its originally meant to be.
The day and month get interchnaged.

Any reason as to why this is happening?

---

### Post by efflandt on 2017-07-14
It might depend whether one or the other system or program settings are in US or European format. Not sure if separators make a difference, but US dates are typically month day year and European dates are commonly day month year (maybe month/day/year vs. day-month-year). So I am guessing it might be a difference in LOCALE settings in each OS. But if you do not set a specific date format for those cells, it might just be the default date format that each uses.

---


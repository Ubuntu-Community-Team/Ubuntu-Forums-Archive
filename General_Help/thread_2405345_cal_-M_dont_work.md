---
title: "cal -M dont work"
date: 2018-11-04
forum: General Help
---

### Post by cosy2 on 2018-11-04
from man pages >  -M      Weeks start on Monday.


```
$ cal -M
Usage: cal [general options] [-jy] [[month] year]
       cal [general options] [-j] [-m month] [year]
       ncal -C [general options] [-jy] [[month] year]
       ncal -C [general options] [-j] [-m month] [year]
       ncal [general options] [-bhJjpwySM] [-H yyyy-mm-dd] [-s country_code] [[month] year]
       ncal [general options] [-bhJeoSM] [year]
General options: [-31] [-A months] [-B months] [-d yyyy-mm]

```

works on ncal

```
$ ncal -M
    Noviembre 2018    
lu     5 12 19 26   
ma     6 13 20 27   
mi     7 14 21 28   
ju  1  8 15 22 29   
vi  2  9 16 23 30   
sá  3 10 17 24      
do  4 11 18 25      

```

---

### Post by Holger_Gehrke on 2018-11-04
'cal' and 'ncal' are actually the same program. Depending on whether it's called as 'ncal' or through the symbolic link 'cal' it accepts the new options (like -M) or it does not, behaving like the traditional Unix tool 'cal'. Admittedly the man-page should be clearer on what is a new option and what is traditional

Holger

---

### Post by cosy2 on 2018-11-05
strange because i am quite sure it work the correct way on archlinux

---


---
title: "gnuplot: How to plot columns with headers as filenames?"
date: 2014-01-18
forum: General Help
---

### Post by aalunga on 2014-01-18
I am using gnuplot for plotting data. I have a specific  problem.


  I have a data file which has titles in its first row.  I want to  generate separate plots  for each data. Each  plot should be named after  its header. 
  Say, for instance


  TIME    DISPLACEMENT   VELOCITY   ACCELERATION 
0        0        15          0 
1        10       100        5


  set terminal png
set output "[B][I].png" 
plot for [i=2:4] *[/I][/B] using 1:i

  
I need the output of 1:2 as DISPLACEMENT.png, 1:3 as VELOCITY.png, etc.

  Is there any way of doing it??

---


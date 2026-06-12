---
title: "Is There an Easy Way to Create a Timeline in Oo or Linux in General?"
date: 2007-05-30
forum: General Help
---

### Post by SendDerek on 2007-05-30
Hey All.

I just spent the past hour trying to figure out how to create a nice timeline in Open Office Calc (Spreadsheet).  Basically, what I'm trying to do is create a timeline of processor clock speeds from 2000 to 2007.  I would like it to illustrate how the clock speeds haven't really evolved as much from 2005 to 2007 as they had from 2000 to 2005.

Does anybody have any suggestions?  Here is my data:
```

Month/Year      Clock Speeds
Jan. 2000	800
March 2000	1000
Nov. 2000	1500
April 2001	1700
Aug 2001	2000
Jan. 2002	2200
June 2002	2530
Aug 2002	2800
Nov. 2002	3000
June 2003	3200
June 2004	3600
Jan. 2005	3800
Today 2007	3800

```
Thanks for any help!

-Derek

---

### Post by swisscow on 2007-05-31
Hi, just had a go with your data

I just used the chart function in office and picked a line graph.

 Seems a fairly linear increase to me

---

### Post by SendDerek on 2007-05-31
Yeah... that's the problem, I really don't think it should be that linear.

If we take a two year period of time, say 2000 to 2002 , the processor speeds go from 800 to 2200 (1400 difference).  But, if we take the same two year period of 2005 to 2007, processor speeds have been the exact same (3800) with no increase.  That's what I wanted this line graph to show.

---

### Post by swisscow on 2007-05-31
Thr problem I see is that the time periods between readings are not consistent. I've knocked up this quick (and I mean quick) spreadsheet with a bar graph - interpolate what you will. The way I see it is that clock speeds rose fairly linearly and then hit the 3500 mark or so and stopped over the last couple of years - but there is a lot of data missing. 

Hope it helps

---

### Post by SendDerek on 2007-06-09
I just wanted to say that I sure appreciate your help, swisscow.  I did find a solution that works for me.  I created the x-axis by counting from 0 to 70 months in groups of 5 (0,5,10,15...) and this seemed to portray exactly what I wanted!

Thanks so much for you help!

---


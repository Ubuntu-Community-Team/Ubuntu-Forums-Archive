---
title: "Any OpenOffice.org Calc wizards in here?"
date: 2007-05-09
forum: General Help
---

### Post by Lux Perpetua on 2007-05-09
I have my students' grades in an openoffice spreadsheet. Each row corresponds to a student, and let's say each column corresponds to a quiz. The final quiz grade for each student will be computed by taking the mean of the quiz grades, *omitting the lowest two grades*. Example:

```
  A			B	C	D	E	F	
			Quiz #1	Quiz #2 Quiz #3	Quiz #4	Quiz #5
1 Christy Canyon	4	8	1	10	9	
2 John Holmes		10	10	8	0	0	

```Suppose all quizzes are out of ten points. Then Christy's quiz average is (8/10 + 10/10 + 9/10)/3 = 0.9 (the 1 and the 4 are omitted), and John's quiz average is (10/10 + 10/10 + 8/10)/3 = 0.933 (the two zeroes are omittted). 

What I've done in the past is write an external program to do this, feed the grades to that program, and paste the output back into my spreadsheet, but that has its disadvantages. It'd be nice if I could do this all with a formula in Calc itself. Can anybody suggest a method? An equivalent problem that's easier to describe is sorting the values in each row of a spreadsheet independently. If I could even do that easily, I'd be set.) 

If it helps, my OpenOffice.org version is 2.0.2.

---

### Post by laidback on 2007-05-09
Yes it seems possible.
For simplicity create  additional columns called Lowest 1, Lowest 2, Modified Total, Score

Name	b	c	d	e	f	lowest 1	lowest 2	Modified Total	Score
Fred	1	4	7	3	8	1	3	19	6.33
Charlie	8	6	7	4	3	3	4	21	7

(sorry if formatting has gone off I don't know how to retain it)
Lowest 1 =SMALL(B2:F2;1) in row 2    (this function picks the first smallest between B2 and F2)
Lowest 2 =SMALL(B2:F2;2) in row 2    (this function picks the second smallest between B2 and F2)
Modified Total  =SUM(B2:F2)-SUM(G2:H2) in row 2
Score  =I2/3 (that's column I row 2 divided by 3) in row 2 i.e. the Modified Total / 3

copy down for more rows

This could be simplified into fewer columns, but then it wouldn't be so easy to understand or check.

Laidback


PS Please let me know how you create the formatted grey section in your question

---

### Post by Lux Perpetua on 2007-05-09
> **laidback said:**
> Yes it seems possible.
For simplicity create  additional columns called Lowest 1, Lowest 2, Modified Total, Score

Name	b	c	d	e	f	lowest 1	lowest 2	Modified Total	Score
Fred	1	4	7	3	8	1	3	19	6.33
Charlie	8	6	7	4	3	3	4	21	7

(sorry if formatting has gone off I don't know how to retain it)
Lowest 1 =SMALL(B2:F2;1) in row 2    (this function picks the first smallest between B2 and F2)
Lowest 2 =SMALL(B2:F2;2) in row 2    (this function picks the second smallest between B2 and F2)
Modified Total  =SUM(B2:F2)-SUM(G2:H2) in row 2
Score  =I2/3 (that's column I row 2 divided by 3) in row 2 i.e. the Modified Total / 3

copy down for more rows

This could be simplified into fewer columns, but then it wouldn't be so easy to understand or check.

Laidback


PS Please let me know how you create the formatted grey section in your questionExcellent! This will do exactly what I need. I didn't know about the SMALL function. What I'm using now is ```
(SUM(BJ2:BU2)-SMALL(BJ2:BU2;1)-SMALL(BJ2:BU2;2))/10
```

To answer your question, here's how to post text with preserved formatting: > [code**]Your text here[/code**]

---

### Post by laidback on 2007-05-09
```

Name	a	b	c	d	e	lowest 1	lowest 2	Modified Total	Score
Fred	1	4	7	3	8	1	3	19	6.33
Charlie	8	6	7	4	3	3	4	21	7


```

Does that look better?

Glad the functions work. Once you're satisfied it's much neater the way you have it.

If you need functions try Insert>Functions  then search through the various options.

PS
Formatting not very good is it....oh well try again some time. Thanks for the tip

---


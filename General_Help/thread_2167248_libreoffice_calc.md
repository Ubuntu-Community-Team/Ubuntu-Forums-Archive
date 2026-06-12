---
title: "libreoffice calc"
date: 2013-08-13
forum: General Help
---

### Post by TheodoreP on 2013-08-13
I'm sorry if this posted in the wrong section, but I don't know where else to post it. I'm trying to automate a payroll card for my work and I can't seem to figure out how to define a format for am and a format for pm. As well, I'm in need of help figuring out a formula for figuring the total hours for each day, but let's focus on the formatting first.

---

### Post by grahammechanical on 2013-08-13
I found this in Libreoffice Help under times in cells.
> 
   [SIZE=2]If you want to calculate time differences, for example, the time between 23:30 and 01:10 in the same night, use the following formula:
[/SIZE]
[SIZE=2] [/SIZE][SIZE=2]=(B2<A2)+B2-A2

[/SIZE]
[SIZE=2] [/SIZE]The later time is B2 and the earlier time is A2. The result of the example is 01:40 or 1 hour and 40 minutes.

 In the formula, an entire 24-hour day has a value of 1 and one hour has a value of 1/24. The logical value in parentheses (round brackets) is 0 or 1, corresponding to 0 or 24 hours. The result returned by the formula is automatically issued in time format due to the sequence of the operands.



I have to go out shopping now so I can not show you the results of my experiments. But i can be done.

regards.

---

### Post by TheodoreP on 2013-08-13
That helps a little, but I'm not using military time for this I am using am/pm time.

To help you understand what I'm trying to do I'm attaching a screen shot of my document.

---

### Post by John_McCourt on 2013-08-14
Sounds like homework

---

### Post by Ninja&gt;Master on 2013-08-14
> **John_McCourt said:**
> Sounds like homework

He said its for work

> 
[COLOR=#000000]I'm sorry if this posted in the wrong section, but I don't know where else to post it. I'm trying to automate a payroll card [SIZE=4]**for my work**[/SIZE] and I can't seem to figure out how to define a format for am and a format for pm. As well, I'm in need of help figuring out a formula for figuring the total hours for each day, but let's focus on the formatting first.
[/COLOR]

---

### Post by grahammechanical on 2013-08-14
> I'm not using military time for this I am using am/pm time.

Yes, I know but for some calcuations with time it is better to use 24 hour input. In Libreoffice Calc go to Format>Cells>Time and select 01:37PM from the menu and by entering time as hh:mm it will display as Am or PM. For example, 08:30 appears as 08:30 AM and 17:30 appears as 05:30 PM. Now if you put that formula in the Daily totals cell and the cell is format Time> 13:37 you will see 09:00 appear as the total hours worked.

But that includes breaks which may be unpaid. So, if you include a cell for Breaks  and a cell for Paid for and format 13:37 and you can deduct the break time from the daily totals and end up with the time to be paid for.

Example.

Cells A1 = In  B1 = Out  C1 = Daily Totals   D1 = Breaks   E1 = Paid for

Cell format

format 01:37 = A2 & B2   format 13.37 = C2, D2 & E2

cells with formula C2 has =(B2<A2)+B2-A2  E2 has =C2-D2

Data entered into cells  C2 has 08:30, B2 has 17:30 & D2 has 0:30

Results on screen

In (cell A2) has 08:30 AM  Out (cell B2) has 05:30 PM, Daily totals (cell C2) has 09:00 Breaks (cell D2) has 00:30, Paid For (cell E2) has 08:30.

Now it get tricky if we want to work out how much money should be paid. I have not got the right just yet. I think that the hours worked will have to be converted to minutes worked and the rate of pay per hour will have to be converted to pay per minute and then one is multiplied by the other.

Anyway this is enough to show how it is done and remember I am just experimenting. And then you could see if you could make use of or modify one of these templates

[http://templates.libreoffice.org/template-center](http://templates.libreoffice.org/template-center)

Regards.

---

### Post by bapoumba on 2013-08-14
Moved to General Help.

---

### Post by zacktu on 2013-08-14
I did an experiment with LO calc.  I formatted two cells, A1 and B1 as with Format/Cells/Numbers/Time to be 1:37 PM.  I formatted C1 with Format/Cells/Numbers/Time to be 01:37.  I entered 
A1 as 9:45 PM
B1 as 12:30 AM
C1 as B1-A1
The difference is 02:45.  That's the answer I would get if I were calculating with pen and paper.  Is that what you want?

---

### Post by TheodoreP on 2013-08-14
> **zacktu said:**
> I did an experiment with LO calc.  I formatted two cells, A1 and B1 as with Format/Cells/Numbers/Time to be 1:37 PM.  I formatted C1 with Format/Cells/Numbers/Time to be 01:37.  I entered 
A1 as 9:45 PM
B1 as 12:30 AM
C1 as B1-A1
The difference is 02:45.  That's the answer I would get if I were calculating with pen and paper.  Is that what you want?

Ok, that helps a little though, how would I do that with two in and two out columns.

---

### Post by Vaphell on 2013-08-15
the same, OUT1+OUT2-IN1-IN2

---

### Post by TheodoreP on 2013-08-15
I thank you that is what I what I was after!

---

### Post by welefort on 2014-02-26
> **Vaphell said:**
> the same, OUT1+OUT2-IN1-IN2


Hello, I know this is a solved issue, but it does relate to the problem Im having.  I noticed that in your example you were able to get the hours worked in a readable format.. 9.5  8.5..etc,  well i've been unable to get that correct formation.. 

 As you can see, my total hours for the day keep coming up as "times"  and not just a number of hours.  Also my "Current"  Which would be a total of all the hours, is displayed in time format.  I cant seem to find the correct format..or correct formula to give me a hours difference..

My Example.  Its a time Keeping sheet for some hours I need.
[IMG]http://i.imgur.com/EkVSPYk.png[/IMG]

---


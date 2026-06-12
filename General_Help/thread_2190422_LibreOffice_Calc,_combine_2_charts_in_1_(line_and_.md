---
title: "LibreOffice Calc, combine 2 charts in 1? (line and column/bars)"
date: 2013-11-27
forum: General Help
---

### Post by Niemil on 2013-11-27
I started use LibreOffice calc yesterday, I never really been using it before. Looks familiar to Microsoft Excel, but I also got not much experience with Excel [I](used it many years ago though, but forgot most of stuffs, and were just plain simple stuffs).
[/I]
Yesterday night I finally managed to do a graph which I wanted, a graph that shows my weight change over time with also a line that shows an average curve on each week.
However, I got one thing missing left out that I really want. It's a column (bars) that I want to show the amount of calories I have intake *(or I think of doing calories deficit, but that I can decide later anyway).*

Here is really a great example where they've done it
[IMG]https://dl.dropboxusercontent.com/u/640925/kolozzeum/journal/vikttrend131124.PNG[/IMG]

Simply those thin lines underneath, and with those values on the right side.

Now, how do I do this in LibreOffice Calc?
My graph currently looks like this:
[IMG]http://i.imgur.com/tQcgAHj.png[/IMG]

Now, how do I do like the example I had there above?

If you wanna check how I built up this, I also attaching the LibreOffice calc file.

---

### Post by amanchesterman on 2013-11-27
The simple way: put your data in (say) three adjacent rows in your spreadsheet, highlight all three rows of data and then click the Chart Wizard icon on the toolbar. When the wizard pops up choose:
- chart type: column and line (the bottom option) and select the 'number of lines' appropriately (you want two lines, which will leave one data series to be displayed as columns) 
- data range: 'data series in rows'. (If your data are in adjacent columns rather than rows on your spreadsheet, select 'data series in rows' instead.)

You may need to experiment to get it exactly as you want it. If you click on a data series on the graph you can re-invoke the wizard at any time.

Hope that helps!

---

### Post by Niemil on 2013-11-27
Thanks!

BUT! I have no idea how to change this, currently the weight itself are on columns, I cannot see where I can change this so the calories takes the columns place?
Looks like this: [http://i.imgur.com/WEF83AE.png](http://i.imgur.com/WEF83AE.png)

---

### Post by amanchesterman on 2013-11-28
Well I've never done it myself so I'm not the best person to advise. But when I tried it out yesterday, it seemed that Calc displays the first data series as columns (as in your example) and the latter two as lines -- so if I were in your shoes, experimenting, I would simply move the third column of data (your calorie intake) into the first column and see if that helps.

Also, depending on the numbers involved, you may need to display the different data series against different scales on the Y-axes -- since your weight measured in kilograms will be a different order of magnitude from your calorie intake measured in kCal? There is a helpful worked example of how to do something like that here:
[https://forum.openoffice.org/en/forum/viewtopic.php?f=75&t=27407](https://forum.openoffice.org/en/forum/viewtopic.php?f=75&t=27407)

(Yes, I know that forum is about Open Office Calc rather than Libre Office Calc -- but OO and LO are very similar, and the methods for one often work with the other. Moreover you are likely to get more help if you post in the specialist OO or LO forums when you are asking tricky questions about graphs etc. since **this** forum (the Ubuntu one) is mainly for questions about the operating system.)

---

### Post by Rex Bouwense on 2013-11-28
You will probably get a solution if you go to their forum.

[http://en.libreofficeforum.org/](http://en.libreofficeforum.org/)

---


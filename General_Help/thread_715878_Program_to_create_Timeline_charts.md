---
title: "Program to create Timeline charts ?"
date: 2008-03-05
forum: General Help
---

### Post by Jingo on 2008-03-05
Does anyone know of a program which can create Timline Charts ?

This is what I would like:
[IMG]http://www.vertex42.com/ExcelArticles/Images/timeline/Timeline-for-Benjamin-Franklin.gif[/IMG]
From: [http://www.vertex42.com/ExcelArticles/create-a-timeline.html](http://www.vertex42.com/ExcelArticles/create-a-timeline.html)

This was made in Excel, but I haven't figured out how to make it in OO.o.

Any program dedikated for this ?

/Jingo

---

### Post by rsay on 2008-03-05
Jingo,

openoffice works fine for this sort of application. In fact, the charting part of oo has been improved just recently. The example you gave is just an xy scatter plot with data labels and error bars. I didn't understand all the formulas in the tutorial that you referenced but I was able to pretty much follow the instructions on the web page and create a similar chart. I started with the template on the page that you referenced and opened with oo-calc

1. Start chart wizard
2. Select XY scatter (next)
3. Data range B5-E19,  unselect first row as label, unselect first column as label (next)
4. Data labels C5-C19 (next)
5. Add title, unselect legend and unselect y axis grid (finish)
6. Right click one of the data points(yellow triangle), object properties, data labels tab, select show label text
7. Statistics tab, error indicator, select lower indicator
8. statistics tab, select percentage, set at 100
9. right click y axis, object properties, labels tab, unselect show labels

You can then play around with the line styles, fonts, colors and markers until it looks pretty to you. I had to add leading spaces on the data labels to get them to right justify like in your example but maybe somebody better with spreadsheets could figure that out in a way thats more automated.  If you play around with the chart tool for a while you can probably make something very cool.

---


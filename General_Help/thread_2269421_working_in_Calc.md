---
title: "working in Calc"
date: 2015-03-15
forum: General Help
---

### Post by trav9595 on 2015-03-15
I have a Calc document. It has about 7 columns. One of the columns has an extra word at the beginning of the field. I need to make a new column that has only that word in it. Then I can delete that column. So I would be splitting a column into 2 columns. How do I do that??

---

### Post by steeldriver on 2015-03-15
You should be able to insert an empty colum to the right of the column whose field you want to split out, then select the column you want to split and use 'Data' --> 'Text to Columns...' and fill in the dialog accordingly (it's hard to be more specific without seeing your data: you probably just need to choose 'delimited' and 'space')

---

### Post by Holger_Gehrke on 2015-03-15
Go to the first free column to the first line of data. Enter a formula like
```

=LEFT(A1,SEARCH(" ",A1))

```
Instead of A1 use the column you want to split and the line the formula is in. You should now see the first word in that cell. Copy the formula to all lines in this column. Mark all the cells with the formula in it and copy them. Go to the top of the next column, right click and select "Paste Special". In the "Selection"-part of the dialog, deselect everything but "Text" then click 'OK'. You can now remove the column with the formula and the original data column and move the pasted column to the place of the original data if you want to.

---


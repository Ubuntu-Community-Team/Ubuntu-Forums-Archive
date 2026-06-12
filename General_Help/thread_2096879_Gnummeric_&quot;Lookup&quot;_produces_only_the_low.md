---
title: "Gnummeric: &quot;Lookup&quot; produces only the lowest/last possible result"
date: 2012-12-21
forum: General Help
---

### Post by Pat Guano on 2012-12-21
Good afternoon.

I cannot find a better forum for questions on Gnome-Office, sorry.

In a Gnumeric 1.10.17 workbook of two tables, I enter the formula 
[COLOR=Navy]***=lookup($A$1;Journal!$C$3:$D$65536;Journal!$B$3:$B$65536)***[/COLOR]
in the cells of a column.

The value from A1 is found many times in the range *Journal!$C$3:$D$65536* and the values in *Journal!$B$3:$B$65536 *are of big diversity.

However, the result in ALL cells that contain the formula is always the same and always the very last possible value from the target range.

How do I have to modify my formula to have all result-values displayed ?

Thank youhou.
EDIT: Ignore the final space in the formula, it is not present in the editor, if I am not dreaming.

---

### Post by Pat Guano on 2012-12-23
I understand I misinterpreted the lookup() function and that in Gnumeric there is currently no simple way to extract *all* the results that I am after. I might try to develop such a function in Python.

But for the time, this issue can be ignored.

Thank you anyway.

---


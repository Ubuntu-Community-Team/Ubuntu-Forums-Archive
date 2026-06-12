---
title: "LibreOffice Calc macro documentation Numberformat"
date: 2013-05-11
forum: General Help
---

### Post by col48 on 2013-05-11
I can't get on to the LibreOffice forum (the passwords they send me are not recognised), so I'm asking here, more for the sake of anyone else who might want the information than my own.

LibreOffice 3.5.7.2 in 64bit Precise.

I have a Calc spreadsheet with one macro in LO Basic (the only one I expect ever to need to write!), originally written years ago for OpenOffice.
It calculates a lot of numbers which are then used to populate many cells - a variable number of them and in locations which are themselves not fixed.  Partly because the sheet is hand-edited between macro runs, the macro itself needs to fix the cell format, and to do this it uses a statement like

```
 gSheet.getCellByPosition(i%, j%).NumberFormat = sharedformat%
```

where sharedformat% is a constant declared once so that all the cells the macro writes are guaranteed the same format.  There are others it merely reads which have different numeric formats, so a global operation is inappropriate.

I have not been able to find any documentation for this integer style of setting formats, and it seems that the LibreOffice values are not the same as the OpenOffice (or perhaps are not handled identically).
**[SIZE=3]If anyone knows where to find a list, maybe they could post a link?[/SIZE]**

Incidentally, I found the value I needed by formatting a cell as I wanted it manually and then checking the value of NumberFormat before the macro changed it.

---

### Post by col48 on 2013-05-19
No replies - I think this must be the duckbilled platypus of the LibreOffice environment!!!

---


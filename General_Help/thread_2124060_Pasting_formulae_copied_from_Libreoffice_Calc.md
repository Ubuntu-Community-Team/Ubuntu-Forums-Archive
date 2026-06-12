---
title: "Pasting formulae copied from Libreoffice Calc?"
date: 2013-03-09
forum: General Help
---

### Post by newboon2 on 2013-03-09
[FONT=Times New Roman][SIZE=3]In Microsoft Excel, I can use “View” > “Show Formula”, copy some cells, switch to a text editor or some other programme and “Paste”, causing any given formula in the source to be pasted as a formula.[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]When I try to do this in Libreoffice Calc (v3.5.x that came with Ubuntu 12.10), it only pastes cells' values. Pasting elsewhere in Calc works as expected, pasting the formula (with references adjusted relative to the destination cell) so the equations must still be in the clipboard somewhere.[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]What am I doing wrong? How can I copy formulae from a range of cells and paste the formulae instead of the values?[/SIZE][/FONT]

Thanks.

---

### Post by The Cog on 2013-03-09
Normally, you just copy and paste the cells that contain formulae. As you paste the cell, the formula get adjusted to retain relative cell reference positioning. No need to do "show formulas".

---

### Post by newboon2 on 2013-03-09
> **The Cog said:**
> Normally, you just copy and paste the cells that contain formulae. As you paste the cell, the formula get adjusted to retain relative cell reference positioning. No need to do "show formulas".
Thank you for taking the time to respond.

I guess I'm not expressing myself very well. What I want is to paste the formulae themselves.
In Excel, if you copy normally and paste into a text editor eg. notepad on Windows or TextEdit on OS X, it will paste values. However, if you switch modes by selecting "View" > "Show Formula", then perform the copy, the formula gets pasted at the destination.

In Calc, this doesn't happen, and the value gets pasted no matter what.

---

### Post by The Cog on 2013-03-09
Not for me. I just tried this: 
In column A I put 4 cells containing 1, 2, 3, 4.
in cell B1 I put the formula =a1*2
Copy B1 and paste into B2: shows 4
Copy B1 and B2, paste into B3: B3,B4 show 6,8
Clicking on any of the column B cells shows the formula in the edit bar

---

### Post by newboon2 on 2013-03-09
> **The Cog said:**
> Not for me. I just tried this: 
In column A I put 4 cells containing 1, 2, 3, 4.
in cell B1 I put the formula =a1*2
Copy B1 and paste into B2: shows 4
Copy B1 and B2, paste into B3: B3,B4 show 6,8
Clicking on any of the column B cells shows the formula in the edit bar
I appreciate the effort you are putting into testing this, but once again it appears I have failed to convey the issue I'm trying to resolve.

Pasting within Calc is working for me as I originally posted.

The problem appears when attempting to paste into some other programme.
Taking your example:
> Copy B1 and paste into B2: shows 4
I would like to copy B1 and paste into gedit and see "=a1*2", not "4".

Similarly,
> Copy B1 and B2, paste into B3: B3,B4 show 6,8
I would like to see pasted into a text editor:
=a1*2
=a2*2

Thanks.

---

### Post by The Cog on 2013-03-09
Doh! I should go back to school and learn to read properly. I understand now. Thanks for being so gentle with me.

Sadly, I can't help. I can't find a way to copy the formulae out except by copying them one by one from the formula bar. I can't even find anything like a "view formulae" option or even a way to copy/paste into a spare sheet so that it shows the formulae.

Edit:
The best I can find is to export to CSV - the export dialog gives you an option to export as formulae instead of numbers. You could then copy/paste the text file.

---

### Post by newboon2 on 2013-03-09
> **The Cog said:**
> The best I can find is to export to CSV - the export dialog gives you an option to export as formulae instead of numbers. You could then copy/paste the text file.
Ahhh, I didn't know you could do that.

It isn't ideal but it's a good enough workaround for what I need.

Thank you very much!

---

### Post by Vaphell on 2013-03-09
you could also use =formula(cell) to produce cells with text representations of formulas (formula() returns a text string). Copy pasting these values would give you what you want at the expense of additional temporary cells.

---

### Post by newboon2 on 2013-03-09
> **Vaphell said:**
> you could also use =formula(cell) to produce cells with text representations of formulas (formula() returns a text string). Copy pasting these values would give you what you want at the expense of additional temporary cells.
Thank you, I was not aware of the "formula()" function. I was able to get the desired result by incorporating it into a more complicated expression (although I suspect there may be overlooked exceptions):

```
=IF(A1="","",IF(ISERROR(FORMULA(A1)),A1,FORMULA(A1)))
```

As it turns out, I found out how formulae can be copied within calc, and I suspect the current behaviour is actually a bug. Setting "Tools" > "Options" > "LibreOffice Calc" > "View" and checking the "Formulas" checkbox causes Calc to display formulae by default, and copying copies formulae (which is what I want).

As is the case when the checkbox is unselected, it is possible to toggle the view mode (values vs. formulae) using the "View" > "Show Formula" menu, but again this has no effect on what is copied, in this case copying the formula regardless of what is showing and now it becomes impossible to paste values into external programmes (equally annoying).

My suspicion is that the expected behaviour is that toggling the menu should also toggle what is copied to the clipboard, the same way that Excel does it.

Anyway, thanks to you both for your input.

---

### Post by vanadium on 2013-03-10
When I turn on "Show formula's", I can copy the formula's as such to an editor. This is version 4.0.1.2, though so this may be something that has addressed in the latest Libreoffice release.

---


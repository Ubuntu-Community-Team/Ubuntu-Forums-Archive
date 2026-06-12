---
title: "Terminal Command, Open Specific Sheet"
date: 2016-12-27
forum: General Help
---

### Post by Quarkrad on 2016-12-27
Running 16.04.   I use the following to open a spreadsheet:  libreoffice -o ~/Desktop/test.ods .  If a have three sheets in that workbook, say a, b, and c - is there a command I can use to launch the spreadsheet showing a specific sheet?

---

### Post by Keith_Helms on 2016-12-27
No.

---

### Post by dragonfly41 on 2016-12-28
You can try opening your spreadsheet and then applying automation script.
e.g. F5 launches the spreadsheet navigation window.   
So consider what key sequence will get you to Sheet1, Sheet2, Sheet3?
Tools such as Actionaz and xdotool might then help to automate clicking on Sheet1, Sheet2, Sheet3 using key press emulation.

---


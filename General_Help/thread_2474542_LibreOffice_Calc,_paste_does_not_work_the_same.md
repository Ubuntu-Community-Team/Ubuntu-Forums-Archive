---
title: "LibreOffice Calc, paste does not work the same"
date: 2022-05-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2022-05-02
I upgraded from 20.04 to 22.04 and the version of LibreOffice calc does not let me paste formulas like i could before, i just paste the evaluated data, not the formula

i have a spreadsheet with this formula in one column _[FONT=courier new]=IF(AND(ISBLANK(F22),ISBLANK(G22))," - ",OFFSET(H22,-1,0,1,1)+G22-F22)[/FONT]_ and when i insert few new rows and copy/paste the cells with the formula 

note that the checkbox for evaluate formulas being checked or uncheck has no effect, aside from rewrite the formula for every cell with new numbers for the new row is there another way to paste these formula and have it auto update the row number

---

### Post by spjackson on 2022-05-04
While this doesn't really solve your problem, I will just say that on a fresh install of 22.04 I am not seeing the behaviour you describe. As far as I can tell, paste is the same as on 20.04: a formula is pasted as a formula, with rows changed where appropriate.

---

### Post by pqwoerituytrueiwoq on 2022-05-05
can try it with this document: [https://www.vertex42.com/Files/download2/odf.php?file=checkbook-register.ods](https://www.vertex42.com/Files/download2/odf.php?file=checkbook-register.ods)

---

### Post by spjackson on 2022-05-06
> **pqwoerituytrueiwoq said:**
> can try it with this document: [https://www.vertex42.com/Files/download2/odf.php?file=checkbook-register.ods](https://www.vertex42.com/Files/download2/odf.php?file=checkbook-register.ods)
Yes, that works for me on 22.04. Inserted 2 rows above where it says "Insert new rows above this line", copied (Ctrl-C) cell H35, highlighted cells H36 and H37 and pasted (Ctrl-V). The formula is inserted into the new cells with the row numbers updated, as expected.

---

### Post by pqwoerituytrueiwoq on 2022-05-06
How is this not working for me...

guess i will record this with OBS

[https://www.mediafire.com/file/wbjxqm7b0wmbfxk/2022-05-06+09-05-09.tar.gz/file](https://www.mediafire.com/file/wbjxqm7b0wmbfxk/2022-05-06+09-05-09.tar.gz/file)

Version: 7.3.2.2 / LibreOffice Community
Build ID: 30(Build:2)
CPU threads: 12; OS: Linux 5.17; UI render: default; VCL: kf5 (cairo+xcb)
Locale: en-US (en_US.UTF-8); UI: en-US
Ubuntu package version: 1:7.3.2-0ubuntu2
Calc: threaded

---


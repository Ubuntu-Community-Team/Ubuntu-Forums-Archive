---
title: "Wine Problem"
date: 2007-03-17
forum: General Help
---

### Post by jasonp on 2007-03-17
Hi im quite new to ubuntu but my problem is installed wine thru the terminal with this command : sudo apt-get intall wine that went smooth installed fine but wen i execute a .exe file it says theres no program to run it im confused X:confused:

---

### Post by zanglang on 2007-03-17
Make sure that if you're running it in the console you enter it in this format: "wine <correct path to .exe>". If the program is in your .wine's virtual C: drive you can type it in Windows' style, e.g. wine "C:\Program Files\test.exe". The double-quotes are important!

---

### Post by zvacet on 2007-03-17
Did you done this 
```
winecfg
```
If you do put exe you want to run in C drive in .wine folder(hidden folder in your home directory),and after that type in terminal
```
winefile
```
go to C drive>program files>your exe>double click

---


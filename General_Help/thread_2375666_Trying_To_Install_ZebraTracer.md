---
title: "Trying To Install ZebraTracer"
date: 2017-10-26
forum: General Help
---

### Post by braznyc on 2017-10-26
I had it installed on my computer.
I couldn't figure where the ini file was saved.
Then I tried to reinstall it. But it doesn't start.

Any suggestions?

---

### Post by Andrew_Lucas on 2017-10-26
I just Googled it and found this: 

[https://github.com/maxim-s-barabash/ZebraTrace](https://github.com/maxim-s-barabash/ZebraTrace)

From the page there:
> 
ZebraTrace is a simple tool to trace bitmap images into a pattern of curves 
with a variable width. You can control amount of curves, resolution, min and 
max width, functions for plotting the curves.

The application was created primarily for Guilloché pattern design and all 
kinds of creative engraving.

ZebraTrace has a Qt4-based user interface and is written in Python.

How to run:

$ cd src
$ python ZebraTrace.pyw

Edit: you can install python with the command sudo apt install python3 but it should already be installed
Edit 2: you could also make a .desktop file so you could run the command from clicking on an icon. [https://askubuntu.com/questions/476981/how-do-i-make-a-desktop-icon-to-launch-a-program](https://askubuntu.com/questions/476981/how-do-i-make-a-desktop-icon-to-launch-a-program) explains how, use the python command (with the full path, not just the shortened one shown in the quotation) as the Exec line.

---


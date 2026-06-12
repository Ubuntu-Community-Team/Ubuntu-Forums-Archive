---
title: "Ubuntu 13.10 Freeze Problem when maximizing window"
date: 2014-02-01
forum: General Help
---

### Post by tkabir11 on 2014-02-01
[COLOR=#333333][FONT=UbuntuRegular]It doesn't happen always. I've been using Ubuntu 13.10 for few months now- and have been noticing this problem last few weeks only. Sometimes when I try to maximize a window by dragging it to the top edge of screen- I get a freeze. The only thing that moves is the cursor- and I have to hard restart my laptop by long-pressing power button- which damages the hard-drive everytime -_- 
Can I get a fix to this please??[/FONT][/COLOR]

---

### Post by Portaro on 2014-02-01
Probably you have a supercharge in RAM, that makes your pc lost performance,

if you can remember - you install any program on last week ?
can you give more infos about - if your problem appear when you run certainly type of program? example firefox.

You have space on your disk /home, or its full of things?

Try to take a look on htop or top, to see if you have some type of program that invoque / charges much RAM, and in terminal verify - free -m to view what is the ram used on start session and when you use programs that you used constantly, probably you can find what is the problem.

---

### Post by tkabir11 on 2014-02-01
Yes- the windows that have caused the desktop to freeze so far are LibreOffice and qpdf. Never happened with google chrome or mozilla windows. And no- my disk is not even half full.

---

### Post by Portaro on 2014-02-04
**You install any new version of Libreoffice?** in last weeks.

its very strange your problem maybe can be caused by a process (intensity) , a new xorg config or graphic drivers.

---


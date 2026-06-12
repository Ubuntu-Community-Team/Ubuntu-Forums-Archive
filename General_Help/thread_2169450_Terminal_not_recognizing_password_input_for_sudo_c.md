---
title: "Terminal not recognizing password input for sudo commands"
date: 2013-08-22
forum: General Help
---

### Post by Moriel_Yitzhak_Ever on 2013-08-22
For some strange reason, every time I try to send a command with "sudo", when it asks for my password, it doesn't recognize the input.
I know that its not supposed to show the input, so I type my password and click "enter", but it shows that the password is incorrect.
The graphical prompt is fine, just the command-line prompt has problems.
I would like to receive help regarding this issue, as there are some graphical problems (that aren't seen) as well, such as certain settings simply not changing, and such.
Although I'm the one in charge of managing this desktop computer ( as I'm the the only one in the family who understands these things), this is my first Linux distro, Lubuntu 13.04, with LXDE, OpenBox, and GTK+ ( I've only used Windows in the past), so I'm still a noob.
Thank you very much to whomever helps me.

---

### Post by rnerwein2 on 2013-08-22
hi
is it possible that you get anothe langue for the GUI and the SHELL and you have some special character in you password ( like in german: ä,ö ....)
try in a terminal: echo $LANG ?!
ciao

---


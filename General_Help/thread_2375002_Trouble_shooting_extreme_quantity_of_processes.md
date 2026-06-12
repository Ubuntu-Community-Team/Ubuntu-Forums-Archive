---
title: "Trouble shooting extreme quantity of processes"
date: 2017-10-21
forum: General Help
---

### Post by joshualalonde on 2017-10-21
I recently upgraded computers and I'm now running Ubuntu 17.10 with Firefox 56.0 64bit.  As soon as I open firefox with only one blank tab, there are 59 processes running for firefox. That number is not an exaggeration, literally 59. 

Right now I have 4 tabs open and have 69 processes with command..
/usr/lib/firefox/firefox -new-window
running.

30 processes with command
/usr/lib/firefox/firefox -contentproc -childID

27 processes of
/usr/bin/gnome-shell

This is among 756 other processes running.  There is not a single process that does not have at least 4 of the exact process running at once.

Any help would be beyond appreciated.. I hope I provided enough info and if theres anything else you'd like me to add, please ask.

Thanks!

---

### Post by vasa1 on 2017-10-21
As for Firefox, have you tried a new profile without adding any extensions? To do so, close all existing instances of Firefox. *pgrep firefox* should return a blank.

Run *firefox -P* and follow the on-screen instructions.

You could also run *top -bn1* and post the first twenty or so lines, including the stuff at the top.

---

### Post by joshualalonde on 2017-10-21
Well this is a little cleaner.  It would have taken me 20 images to show you my entire top.

Even when I open the calculator it has 4 processes running for it before i even enter a number.

---


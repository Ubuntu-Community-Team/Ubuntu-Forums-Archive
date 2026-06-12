---
title: "xubuntu terminal  reverts  to log in screen"
date: 2007-11-26
forum: General Help
---

### Post by Pointswest on 2007-11-26
I have just installed xubuntu on a 500Mh PIII celeron.  When I try to access a terminal window it reverts back to the log-in screen.  Can anyone direct me to a solution for this problem

Thanks

---

### Post by vambo on 2007-11-26
Sounds very similar to the problem encountered in this thread
[http://ubuntuforums.org/showthread.php?t=602808]("http://ubuntuforums.org/showthread.php?t=602808")
The basic solution was to use an xterm.
Hopefully this helps

---

### Post by Pointswest on 2007-11-28
I tried using the sudo nana /etc/Xll/xorg.conf but only get a message "no such file or dir".  I have also tried the other options from the tab at the bottom of the login  but the same thing happens when trying to use the terminal, it just reverts to the login screen.  I have noticed a lot of commands I use give a reply like this or something like" package not found".  Dont't know what to do now.

An update of this post:  I realize now I was typing the commands for "sudo nano /etc/ X11/xorg/conf" wrong.  Upon using   the correct command, the file is shown in the terminal.  Scroll down to the line that says "Default depth" and change the value from 24 to 16 then save.  This corrected my problem with the terminal screen timing out and reverting to the log-in screen.

Watch your command line execution closely.  Make sure you have not typed an l (L) for a 1 (one)  or o instead of 0 (zero).  Sometimes my unnoticed keystroke errors have led to commands not being executed, be careful.

---


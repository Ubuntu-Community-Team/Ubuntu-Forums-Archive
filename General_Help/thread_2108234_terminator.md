---
title: "terminator"
date: 2013-01-24
forum: General Help
---

### Post by gishaust on 2013-01-24
I have been using terminator for the last couples of days and loving it but I restart my laptop I have to reopen the terminals
the way I like them. Is there a way to save them when I close it down?

---

### Post by furything on 2013-01-24
I would be interested to know if this is possible because when you have multiple open terminals, close them all and start a new session (open a new terminal), the terminal history appears to reflect the history of the last terminal closed from the previous session. Open a second terminal and it has the same history as the last terminal.

You can certainly get a terminal to auto start on reboot. 
[http://askubuntu.com/questions/8834/how-do-i-save-sessions-or-reopen-last-used-applications](http://askubuntu.com/questions/8834/how-do-i-save-sessions-or-reopen-last-used-applications)

In the time spent setting up my system I have used many commands to change access permission/configuration files and unfortunately have lost this history. If I could get this back it would help for any future system build rather than trying to fathom out what I did (my memory is not that great).

Will monitor this thread encase I can get some enlightenment.

---

### Post by percent20 on 2013-01-24
Look into layouts in the terminator config and start options.

for my use i do

terminator --borderless -f 

this doesn't show the chrome and goes fullscreen similar to how my terminal is in mac. 

You can set it to custom layouts you have saved in your config so it will start how you want it to. I haven't played with this much because i use tmux to do all the terminator things just in CLI instead of a GUI.

---


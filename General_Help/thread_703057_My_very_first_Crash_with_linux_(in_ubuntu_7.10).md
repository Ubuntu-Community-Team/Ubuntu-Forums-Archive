---
title: "My very first Crash with linux (in ubuntu 7.10)"
date: 2008-02-20
forum: General Help
---

### Post by Ioky on 2008-02-20
HAHA, yeah as the title say, I finally see a real crash in Linux after using it for like a year and a half. Here is what happen, I was doing my Archit homework with gimp, and I need to go out for dinner, 2 hours later, when I come home, I see the monitor still on, I realize something much going wrong because my monitor will shut by itself after 30 min. So I sit, pass a button on youtube, switch back to the desktop where my works at, and then FreeZE. 

Everything stop responding, kill X wouldn't work, numb lock stop responding, and the sound from youtube reply itself. So after I try everything, I finally ending up press the restart button manually.

I wonder what is really happening, is the system, or the physical computer 's failure causing the crash. I mean after I restart it, it goes back to normal.

---

### Post by socceroos on 2008-02-20
Hmm, that sounds a bit odd.

If you want to know exactly what happened you can view the log files for the computer.

They are located at /var/logs/.

Probably the most useful one will be dmesg.

I don't think you'll understand much of what is going on in the logs unless you get someone to show you 'whats what'.

I hope you didn't lose any work!

---

### Post by buntunub on 2008-02-20
Did you try ctrl+alt+f1 ? If that doesnt work the ctrl+alt+sysreq+RSIUB sometimes works if you possess the kind of manual dexterity it takes to pull that off on the keyboard.

---

### Post by AnRa on 2008-02-21
You may try doing [FONT="Courier New"]Alt + SysRq + R[/FONT], then [FONT="Courier New"]Ctrl + Alt + F1[/FONT], login and type:
```
sudo /etc/init.d/gdm restart
```That will only restart GDM so you can login back and continue using the box. :)

---

### Post by Ioky on 2008-02-21
Yeah, I try everything you have said, the keyboard itself can't even respond. So, I don't think any key would help in this case. Thanks all the help though. Maybe I will go check out the sys log to see if I can found out what happen.

---


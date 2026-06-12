---
title: "What status is after a Ctrl+Alt+F2?"
date: 2015-08-28
forum: General Help
---

### Post by ruwan2 on 2015-08-28
Hi,
When I accidently press 'Ctrl+Alt+F2', it jumps from Ubuntu 12.04 GUI to a full screen black/while text terminal, showing something ...tty4, login:...
Even I have tried several user name at login and password, it refuses to login and says incorrect password. I cannot switch back to the previous GUI. The only way is to Ctrl+Alt+Del warm reboot system.

What status is after a Ctrl+Alt+F2?

Thanks,

---

### Post by The Cog on 2015-08-28
Ctrl-Alt-F7 (or just Alt-F7 actually) shouldl bring you back to the GUI (I have occasionallly seen the GUI on Ctrl-Alt-F8 instead).
Ctrl-Alt-(F1-F6) are all separate consoles - terminal sessions where you can log in as 6 different people if you like. There is usually only one GUI running on terminal 7, but it is possible to begins a second GUI up (for a guest login perhaps?) on Ctrl-Alt-F8 as well.

P.S. 
Occasionally, video driver problems can prevent the GUI restoring properly when you return, leaving you with a black screen.

If you can't log in with your normal username and password, maybe it's an issue with the keyboard layout mapping - the consoles may not have the same keyboard type as the GUI which has its language settings configured in a different place. This would normally only affect punctuation characters etc, not the basic letter layout.

---

### Post by howefield on 2015-08-28
To switch back to your GUI, use Ctrl + Alt + F7

---


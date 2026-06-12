---
title: "I messed up!"
date: 2006-10-21
forum: General Help
---

### Post by Baruch on 2006-10-21
I'm running Kubuntu 6.06. I pressed ALT+CTRL+F1. I thought it would get me a command prompt already logged in as the same user. I got a login prompt (I must have misunderstood somthing someware. If anybody could explain this concept further it would be appreciated).
Anyway, I logged in and tryed to run```
icewm-session -display :1
```I got errors, somthing about X not running. Now I can't get back to KDE! (ALT+CTRL+F7 just puts gibrish on the screen).
HELP!!! ](*,)

---

### Post by raul_ on 2006-10-21
Try ```
xstart
```

---

### Post by bswilson on 2006-10-21
Sounds to me like worst-case scenario, you can just reboot and you'll be fine. 8)

---

### Post by Baruch on 2006-10-21
> **raul_ said:**
> Try ```
xstart
```

Did you meen startx?
It didn't work either.
My main problem is not being able to get back to my KDE. I had a few unsaved things open there!

---

### Post by encompass on 2006-10-21
umm... hard poweroff if you can't get to it... if your running on openoffice or some ofther program it has a rescue feature...
Your graphics driver doesn't like switching to test mode and backk... not good to happen now..
if you do a hard poweroff... like just unpluging the computer... it MAY and I mean MAY giveyou the option to open the file and recover it... but give it about 5 minutes to autosave your work.

---

### Post by bettlebrox on 2006-10-21
Ctrl-alt-F7 (or F8) will bring you back to your X-session.

Your system has up to 6 virtual consoles (Ctrl-alt-F[1-6]) configured by default. U can login in there use the commmand line. But, if X is already running I don't think startx will start another session.

Have a look here at "Section 3.6 Virtual Consoles":

[http://www.debian.org/doc/manuals/debian-tutorial/ch-start.html]("http://www.debian.org/doc/manuals/debian-tutorial/ch-start.html")

(Ubuntu is based on Debian)

---

### Post by emersony on 2006-10-21
Encompass- why can't he just kill pid of the icewm-session ? 

E.

---

### Post by Baruch on 2006-10-21
What?

---

### Post by bettlebrox on 2006-10-22
Oops! Didn't read all of Baruch original question saying ctrl-alt-f7 wasn't working.

Try restarting gdm and see if that works:

sudo /etc/init.d/gdm restart

---


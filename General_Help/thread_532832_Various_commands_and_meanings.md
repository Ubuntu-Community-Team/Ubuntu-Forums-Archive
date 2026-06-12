---
title: "Various commands and meanings"
date: 2007-08-23
forum: General Help
---

### Post by mikex on 2007-08-23
I'm looking for better explanations of these commands and what sequence to use them in to start and stop the X server so I can do an nvidia upgrade better in the future. I managed to do the upgrade, but I futzed around with all these commands in no logical order until I got to the command prompt and stopped the X server. 

ctrl+alt+f1
ctrl+alt+f7
ctrl+alt+backspace
init 3
init 1
gdm stop
gdm start

I would like to know which of these commands do the same thing as others also. I just haven't found a good treatment of these command anywhere yet.

---

### Post by renzokuken on 2007-08-23
**ctrl+alt+f1/f2/f3/f4/f5/f6** all take you to a tty screen

**ctrl+alt+f7** is the virtual terminal on which x runs by default

init 1 and 3 are different run levels, cant remember the difference but one has X the other doesnt

gdm is a process and those two obviously stop and start it

i would have said overall it would be easier to go to a TTY (ctrl+alt+f1-6)

stop X with
```
sudo /etc/init.d/gdm stop
```

perform your upgrade

restart X with

```
sudo /etc/init.d/gdm start
```

then go back to you x screen by pressing Ctrl+Alt+F7

---

### Post by heimo on 2007-08-23
> **mikex said:**
> 
ctrl+alt+backspace

And this one just kills X. I think there's just one reason to use it: if you can't stop X gracefully, for instance, your system gets really stuck and you can't even change to ctrl+alt+F1. Then I hit ctrl+alt+backspace couple times, usually followed by ctrl+alt+del, which will take my system to reboot.

---

### Post by renzokuken on 2007-08-23
> **heimo said:**
> And this one just kills X. I think there's just one reason to use it: if you can't stop X gracefully, for instance, your system gets really stuck and you can't even change to ctrl+alt+F1. Then I hit ctrl+alt+backspace couple times, usually followed by ctrl+alt+del, which will take my system to reboot.

Ctrl+Alt+Backspace actually restarts X, its "gdm stop" and "gdm start" in one go

---

### Post by heimo on 2007-08-23
> **renzokuken said:**
> Ctrl+Alt+Backspace actually restarts X, its "gdm stop" and "gdm start" in one go

I don't think so. But I may be mistaken. Yes, that's the effect if you have gdm running as X will get restarted, but what about if you have started X using startx? Doesn't it just kill it?

EDIT:

Source: [http://www.x.org/archive/X11R6.8.0/doc/Xorg.1.html](http://www.x.org/archive/X11R6.8.0/doc/Xorg.1.html)
> **Ctrl+Alt+Backspace**
Immediately kills the server -- no questions asked.  This can be disabled with the **DontZap** [xorg.conf(5x)]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")  file option.

---

### Post by mikex on 2007-08-24
> **renzokuken said:**
> **ctrl+alt+f1/f2/f3/f4/f5/f6** all take you to a tty screen

i would have said overall it would be easier to go to a TTY (ctrl+alt+f1-6)

stop X with
```
sudo /etc/init.d/gdm stop
```

perform your upgrade

restart X with

```
sudo /etc/init.d/gdm start
```

then go back to you x screen by pressing Ctrl+Alt+F7

Hey thanks, I think that process is what I was looking for.

---


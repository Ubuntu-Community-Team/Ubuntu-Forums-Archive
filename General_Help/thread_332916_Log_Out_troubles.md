---
title: "Log Out troubles"
date: 2007-01-06
forum: General Help
---

### Post by finer recliner on 2007-01-06
I'm currently the only user installed on my computer (dapper drake). I have both gnome and KDE installed.

When i try to log out of gnome, the screen just got blank and i am forced to do a hard restart

crtl+alt+f1 does nothing
crtl+alt+f7 does nothing

i havent tried to log out of KDE

switching users works fine (and then i can log in as the same user on a different DM)

any ideas?

---

### Post by christodoulos77 on 2007-01-06
try:
 ctrl+alt+backspace

---

### Post by finer recliner on 2007-01-06
> **christodoulos77 said:**
> try:
 ctrl+alt+backspace


"THE GOGGLES, THEY DO NOTHING!"


yeahhh ctrl+alt+backspace doesnt do anything.

i also tried logging in and logging out of KDE...which does the same thing

---

### Post by finer recliner on 2007-01-06
bump!

---

### Post by christodoulos77 on 2007-01-07
read this post
 
[http://www.ubuntuforums.org/showthread.php?t=312072](http://www.ubuntuforums.org/showthread.php?t=312072)

it may help

---

### Post by quartzy on 2007-01-07
For KDE you could try doing what I had to do when I had problems with the X server crashing on shutdown:

edit /etc/kde3/kdm/kdmrc

And in the section [X-:*-Core] make this part true:

```
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
TerminateServer=true

```

Worked for me (this is if your using kdm) Maybe a similar thing for GDM

---

### Post by finer recliner on 2007-01-07
> **christodoulos77 said:**
> read this post
 
[http://www.ubuntuforums.org/showthread.php?t=312072](http://www.ubuntuforums.org/showthread.php?t=312072)

it may help


i dont have compiz/beryl installed. and im not trying to disable crtl+alt+backspace


recent update: the last time i tried to log out, it worked. so i logged back into gnome, and about 2 seconds after loading, everything froze except the mouse. ctrl+alt+backspace, ctrl+alt+f1 both didnt do anything. nothing worked except mouse movement.

---

### Post by finer recliner on 2007-01-07
next time it crashes...would it help anyone diagnose the problem if i posted a /var/log file? i dont which one i should look at, or what i would be looking for, but maybe there's something useful in one of those log files?

---


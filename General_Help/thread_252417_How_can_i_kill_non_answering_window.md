---
title: "How can i kill non answering window"
date: 2006-09-06
forum: General Help
---

### Post by eighthate on 2006-09-06
I know Xkill but besides that is there one where i can see live processes? than ks

---

### Post by taurus on 2006-09-06
```
ps -A
```

---

### Post by darkhatter on 2006-09-06
open gnome terminal 
type "ps -A"
then type kill xxxx (whatever the name of the process is)

is that what you are looking for.

or if your in kde you can just hit ctrl+alt+esc
and click the window in question

or you can open process watch program thing forgot the name and that gives you a real time view, sorry I forgot the name of the program (kde user)

---

### Post by eighthate on 2006-09-06
> **darkhatter said:**
> open gnome terminal 
type "ps -A"
then type kill xxxx (whatever the name of the process is)

is that what you are looking for.

or if your in kde you can just hit ctrl+alt+esc
and click the window in question

or you can open process watch program thing forgot the name and that gives you a real time view, sorry I forgot the name of the program (kde user)

THANKS!

---

### Post by darkhatter on 2006-09-06
no problem

---

### Post by jimmygoon on 2006-09-06
You ought to be able to open gnome-system-monitor and or I have more success (it lists more for whatever reason when I use ps -ax)

---

### Post by darkhatter on 2006-09-06
make sure you use a capital "A" and not a lower case

'ps -A' 

not ps -a

---

### Post by Nrvnqsr on 2006-09-06
for a gui version of the command, right-click on any of the top or bottom panels in GNOME and click properties, and there should be a button called "Force Quit" pretty much just click it and select the program you want to kill and verify

---


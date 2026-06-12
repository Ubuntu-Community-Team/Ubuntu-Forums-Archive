---
title: "How do I schedule a file to open every night?"
date: 2007-03-30
forum: General Help
---

### Post by herbster on 2007-03-30
I have a few Excel files I use with OpenOffice that I'd like to have set up to open every night or at certain days of the week, like I did with Vista and XP. How exactly would I do this? I ran Schedule and didn't know what the command was to open an Open Office file (.xls in this case). 

The files are sitting on my desktop.

This would be REALLY appreciated, I need to figure this one out ASAP...

---

### Post by spin2cool on 2007-03-30
The command to launch OO Calc is 'oocalc <filename>'.  Do a search for cron or crontab to see how to set up a scheduled task.  I also believe that there is a gui frontend to crontab called gnome-schedule (or something similar).

---

### Post by herbster on 2007-03-30
spin2cool,

There you go! Hot damn it's the oocalc command I was looking for. Just got it to go.

One thing though, I'm using the Schedule (gui fronted of crontab) and I added 2 tasks so far, and when I did with each one it seems to keep duplicating the task forever unless I start deleting them.. what's up with that??

---

### Post by spin2cool on 2007-03-30
Glad I could help.  FWIW, the other useful OO commands are "oowrite" and "ooimpress".

Sorry - don't know much about the schedule gui program - dig around in these forums or try to find the scheduler project's home page for an FAQ, forum, etc.

---

### Post by enopepsoo on 2007-05-10
> **spin2cool said:**
> Glad I could help.  FWIW, the other useful OO commands are "oowrite" and "ooimpress".

Sorry - don't know much about the schedule gui program - dig around in these forums or try to find the scheduler project's home page for an FAQ, forum, etc.

You can also use this command to open any file with the default program
```
gnome-open
```

Thanks for the tip about gnome-schedule

---


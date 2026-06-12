---
title: "how to restore a hidden window (Conky)"
date: 2007-11-24
forum: General Help
---

### Post by flaggh on 2007-11-24
How do I restore a window that does not appear in my taskbar?  I would like a general solution, but at the moment I'm specifically interested in restoring my conky window.  I've got it all setup and then I managed to minimize it by alt-right click and now I can't figure out how to restore it.  I still see the process running in my system monitor, and I assume I can kill the process and restart it and that will solve my problem no harm done, but I would prefer to know a better solution if this problem ever arose with a program I didn't want to kill and risk losing any unsaved data.

---

### Post by mardawi on 2007-11-24
what are you using? Gnome, KDE, Fluxbox...other?
And why would you need a window for conky anyway?

---

### Post by flaggh on 2007-11-24
I'm using gnome.  Maybe I have the configuration setup wrong but when I run conky, it runs as a pseudo-transparent, borderless window, so I can see the window it creates in the desk panel in the lower-right hand corner even though it does not appear as a normal window.  If I click the show the desktop button, it is minimized as well, however I can restore it by clicking that button again.  But if I alt-right click, the window is minimized and I cannot figure out how to restore it.

---

### Post by flaggh on 2007-11-27
bump

---

### Post by sunzaru on 2008-01-26
I have this problem also.  

In the event i screw up and hit it you can do the following to kill conky and restart it (on all desktops).  You have to kill it otherwise you end up with 2 conkys running (one being minimized and hidden).

ps -edf | grep conk
kill -9 <pid of /usr/bin/conky >       (dont use the <> they are there to show a string encaps.

then relaunch conky

this is what i'm doing until i figure out how to restore this window... bump

---

### Post by sunzaru on 2008-01-26
i found a "cleaner" way to do this.. and it's as easy as 2 clicks  or a cron job can be created but.. here.  (i'm still new to linux so .. bare w/ me)

1. create a new file and open it with gedit.
2. paste the following in, then save and close

```

#!/bin/bash
if [ -n pidof conky ]; then 	# -n tests to see if the argument is non empty
   #echo "the variable X is not the empty string"
   echo "Conky is starting..."
   /usr/bin/conky &
else
   echo "Conky is running."
   echo "Killing conky..."
   killall conky
   echo "Conky is starting..."
   /usr/bin/conky &
fi

```

3. change permissions on the text file so it becomes executable.. chmod 770 Restart-Conky
4. double click on your icon.

It will start if it's not running.  and if it is already running (but hiding) it will killall then start it.

---

### Post by flaggh on 2008-01-28
Thanks for the reply.  I like your solution.  I'll give it a try.

---

### Post by Lunar_Lamp on 2008-01-28
> **sunzaru said:**
> I have this problem also.  

In the event i screw up and hit it you can do the following to kill conky and restart it (on all desktops).  You have to kill it otherwise you end up with 2 conkys running (one being minimized and hidden).

ps -edf | grep conk
kill -9 <pid of /usr/bin/conky >       (dont use the <> they are there to show a string encaps.

then relaunch conky

this is what i'm doing until i figure out how to restore this window... bump

You really should not be using "kill -9" as a default command.  There are virtually no circumstances under which you should be using it in fact.

---


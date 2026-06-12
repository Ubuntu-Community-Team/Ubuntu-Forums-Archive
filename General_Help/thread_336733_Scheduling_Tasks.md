---
title: "Scheduling Tasks"
date: 2007-01-12
forum: General Help
---

### Post by thomasaaron on 2007-01-12
I've written a program that I would like to automatically run every fifteen or twenty minutes.

As far as I can tell, Anacron will only run it once daily, right?

Is there a way configure anacron, or is there another way to make this happen?

Best,
Tom

---

### Post by thoughts on 2007-01-12
What about just using cron?  In a terminal, run "crontab -e" and you can type your command to run, like this:

```

0,15,30,45  *  *  *  *  /home/username/bin/mycommand >/dev/null 2>&1
```

The first 5 columns are minute, hour, day-of-month, month, day-of-week.  The asterisk of course means "all", so this runs the command at the 0th, 15th, 30th, and 45th minute of every hour of every day.  The stuff after mycommand causes all the output to be discarded.

Another method:

```

*/15  *  *  *  *  /home/username/bin/mycommand >/dev/null 2>&1
```

Basically a shorthand way to do the same thing: run the command every 15 minutes.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by thomasaaron on 2007-01-12
OK, I gave that a try but it's not working.

I didn't mention it because I didn't think it mattered, but the program I'm trying to run is python with a Tkinter GUI.  Does CRON just run things in the background, or should it run a GUI?

What I entered was:
0,15,30,45  *  *  *  *  /home/thomasaaron/Programs/WizdomWordz.py

I left off the dev/null part because it's a GUI and has no output (other than the GUI).

What do you think?

---

### Post by thoughts on 2007-01-12
To launch a GUI app from cron, you need to set at least the DISPLAY environment variable first:

```
*/15  *  *  *  *  export DISPLAY=:0 && /path/to/gui-app
```

Give that a try and see how it goes.  Depending on the application, that may be all you need; but some apps may be expecting other env vars to be set.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---


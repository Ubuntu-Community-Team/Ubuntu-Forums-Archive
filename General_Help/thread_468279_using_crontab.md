---
title: "using crontab"
date: 2007-06-08
forum: General Help
---

### Post by littlephil56 on 2007-06-08
I created a small job to test cron.Somehow I don't think it works.This is the content of the cron file:
* * * * * Firefox
but Firefox didn't get executed even once ! 


Is this the correct way to run cron?

---

### Post by jimbob on 2007-06-08
Well, to start with, if the command used Firefox instead of firefox it wouldn't find it.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by littlephil56 on 2007-06-09
Nope,that doesn't help.Should I have to issue any other command prior to this one.

---

### Post by jimbob on 2007-06-09
That command looks like it would constantly spawn instances of Firefox if it was successful since all times are wild cards.
  I don't think you really want that.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by arvevans on 2007-06-09
Are you using "at" to launch your cron jobs, or simply editing your command directly into "/etc/crontab"?  
The menu command located at "/Applications/System Tools/Schedule" will help you launch cron jobs from a GUI front end and is rather easy to use.

if using "at", then try going to a terminal screen, and entering "man at" to see the format and requirements for launching a cron job.  That info also helps if you are directly editing your command into "/etc/crontab".

Arv
_._

---

### Post by pestilence on 2007-06-09
Firefox would not load, since it would request a valid X Session for start, try using lynx for command line browser.
Try creating a script:
firefoxstart.sh:
```

#!/bin/bash
export DISPLAY=:0
/usr/bin/firefox 

```

---


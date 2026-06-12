---
title: "Pidgin"
date: 2007-10-28
forum: General Help
---

### Post by Atzu on 2007-10-28
Pidgin crash after sometime of using it (ubuntu 7.10) dont know why, and its really bothering me 
help me please T_T

---

### Post by Ariox on 2007-11-05
Since updating from Gaim to Pidgin and upgrading to 7.10, Pidgin crashes randomly in the middle of conversations, eventually needing a force quit. Can anyone shed some light onto this problem, perhaps? 

--A

---

### Post by Patiek on 2007-11-07
I had the same problem and had to compile 2.2.2 from source to solve (good so far anyway).

---

### Post by VMOS on 2007-11-13
I'm getting the same problem, it worked when I first used it, but after one restart of my machine it crashes as soon as I try to start it. I uninstalled, reinstalled, compiled from source but same problem.
It's showing as sleeping in resource manager, but nothing else, no errors execpt just now it's popped up "authentication failed"

any ideas anyone?

---

### Post by VMOS on 2007-11-13
right, on a hunch I went and did a search and clicked directly on the BIN file in the folder user\local and it worked.

so then I closed it down and tried it from the launcher in the application menu and that worked as well

so I don't know what's going on really

---

### Post by Lord C on 2007-11-24
When I launch pidgin, it's a 50/50 gamble as to whether it will crash, or sign into my accounts.

I tried upgrading to 2.2.2 but it made no difference.

---

### Post by vreemde eend on 2007-11-29
Hi,

The same problem here. Compiling 2.2.2 from source didn't help. Today there were some updates for pidgin and libpurple, but didn't help either.

Pidgin crashing is enoying, but worse is that it freezes my computer from time to time. Does anyone have a solution for this problem?

thanks a lot

---

### Post by Lord C on 2007-11-29
There was a patch early this morning, I wonder if it fixed things.

Still version 2.2.1 apparently, but we'll see...

---

### Post by kenpody on 2008-02-21
I am not able to launch pidgin from the start up menu or by clicking the icon? does anyone know why? the cursor just spins in circles and then disappears without leaving an error message or anything! I have tried installing the application over and over and the same thing happens.

---

### Post by seventhc on 2008-02-21
> I am not able to launch pidgin from the start up menu or by clicking the icon? does anyone know why?Go to [COLOR=DimGray]*System>Administration>System Monitor *[/COLOR]
Does it show under *Processes*? If so, end it, then try starting pidgin again
If it still fails to start, check processes again to make sure it's still not there, open a terminal and type [COLOR=Indigo]pidgin[/COLOR] and see if it gives errors.

---

### Post by aslamrahman on 2008-02-22
when i type pidgin... the output like that :

pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error

... ??

---

### Post by seventhc on 2008-02-22
from a terminal:
```

sudo apt-get remove pidgin
sudo apt-get purge libpurple0

```

I saw this on another thread about the same problem
[http://ubuntuforums.org/showthread.php?t=680502](http://ubuntuforums.org/showthread.php?t=680502)

---

### Post by buradleix on 2008-02-26
> **Ariox said:**
> Since updating from Gaim to Pidgin and upgrading to 7.10, Pidgin crashes randomly in the middle of conversations, eventually needing a force quit. Can anyone shed some light onto this problem, perhaps? 

--A

Has anyone figured this Pidgin "force quit" and random crashing out? I'm getting tired of crashing in the middle of conversations.

---

### Post by kevdog on 2008-02-28
Why don't you compile pidgin from source?  I think this would most likely solve the problem due to some incompatibility.

---

### Post by Captain Rotundo on 2008-03-03
Compile from source? are you insane? thats the fixed for a standard application in the distribution not working?

I have consistantly had the same problem since the switch to pidgin, it crashes constantly for no reason.

and although I can, I am NOT compiling it from source out of principle.

---

### Post by ifokkema on 2008-03-04
I even had Gaim crash on me frequently... or just suck up 100% CPU for a couple of minutes, so I had to kill it. Upgrading to 7.10 including Pidgin did not help me.

---

### Post by Oldsoldier2003 on 2008-03-04
> **ifokkema said:**
> I even had Gaim crash on me frequently... or just suck up 100% CPU for a couple of minutes, so I had to kill it. Upgrading to 7.10 including Pidgin did not help me.
have you tried a later version from [GetDeb]("http://www.getdeb.net/"), I usually recompile pidgin myself but if you aren't in the mood for it getdeb usually has the latest versions of  common aps.

---

### Post by ifokkema on 2008-03-06
> **Oldsoldier2003 said:**
> have you tried a later version from [GetDeb]("http://www.getdeb.net/"), I usually recompile pidgin myself but if you aren't in the mood for it getdeb usually has the latest versions of  common aps.
Ah....... nice! :)

---

### Post by vikrant82 on 2008-03-06
Most of the times, the hangs are results of naughty plugins.  Like I had a few hangs on music tracker plugin. 

Did anyone notice, pidgin 2.4.0 , in hardy repos is built without SSL/TLS support. It was there with updates 2-3 days back (5th March) . Anyways, had to pick debs from Getdeb. 

Anyways any interesting plugins? I heard about exchange and skype plugins..

---

### Post by pythonusr on 2008-03-06
I built Pidgin from source, and I still get random crashing every once and a while, mid-conversation. I have no plugins enabled besides "Message Notification".

Any other ideas?

---

### Post by kevdog on 2008-03-06
> **Captain Rotundo said:**
> Compile from source? are you insane? thats the fixed for a standard application in the distribution not working?

I have consistantly had the same problem since the switch to pidgin, it crashes constantly for no reason.

and although I can, I am NOT compiling it from source out of principle.

That might be one of the dumbest principles to adhere to!

---

### Post by einstein on 2008-03-09
I could not get Pidgin to do a first start.  Re-installed but no go.  Finally looked up the executable in /usr/bin and ran it from there.

The problem seems to have been that, without any accounts setup and the startup window not opening, Pidgin would just hang for a while then die.

Is okay now.

Edit: Oops, lied.  The reason is worked is because I ran it as root.  So, truth is, in my situation Pidgin works ONLY if run as root.

---

### Post by Oldsoldier2003 on 2008-03-09
> **einstein said:**
> I could not get Pidgin to do a first start.  Re-installed but no go.  Finally looked up the executable in /usr/bin and ran it from there.

The problem seems to have been that, without any accounts setup and the startup window not opening, Pidgin would just hang for a while then die.

Is okay now.
the proper way to start pidgin the first time after an install is to type pidgin in a terminal. after that it installs the menu icons for a gui launch.

---


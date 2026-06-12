---
title: "How do I set system time to UTC (NOT British civil time)?"
date: 2007-07-29
forum: General Help
---

### Post by Thrasyllus on 2007-07-29
How do I select UT (or UTC) instead of British civil time? The selection menu when I installed Feisty only offered the choice of a "national" time, British or Uruguayan or Singapore or whetever. I don't want a national time; I don't live in England. I want straight, vanilla, Universal Time, which just keeps rolling on without daylight saving time or other bureaucratic fiddling. It's scientific, not national, and is the simplest, least confusing time to use if you deal with many different time zones.

---

### Post by davidjmayo on 2007-07-30
Right click on the clock
preferences
choose use UTC

---

### Post by Thrasyllus on 2007-07-30
Thank you David J. 

Do you mean a clock icon? I don't have one! I go to the System Administration settings, select Time and Date, and the menu then asks me for a time zone. There is a long list from Africa at the top to Pacific at the bottom, but no Universal Time, *Where is UTC???*

---

### Post by fjgaude on 2007-07-30
Right-click on the time/date in the panel. If you don't have a panel, what window manager are you using?

frank

---

### Post by Thrasyllus on 2007-07-30
Duh! The digital clock on the panel! Apologies for my stunnedness! 

Okay, that solved a tiny part of the problem. The little clock on the panel now gives me UTC. But if I type the command "date" in a terminal I still get BST, and - more important - any file I create gets timestamped in BST. How can I stop this madness?

---

### Post by davidjmayo on 2007-07-30
EDIIT first try logout and/or restart to see if the setting takes

if not and a warning this is untested but it looks like you do 

```
date -u
```

if you want more info before you try then 
```
date --help
```

or

```
man date
```

seems like you cant configure this option if I read it correctly

---

### Post by Thrasyllus on 2007-07-31
Right... Now, to answer my own question...

First, go to /etc/default/ and edit the file **rcS** by changing the line **UTC=no** to **UTC=yes**. Then invoke **tzconfig**, which will ask if you want to change the time zone. On getting the answer "y" it will ask you to choose from among geographical regions 1) through 11) or "12) None of the above." Answer 12, then select either UTC or Zulu. 

The effect is immediate and survives subsequent reboots. 

I understand the result may be erroneous if the system clock is not itself set to UTC, but such was not my problem.

---

### Post by nick4mony on 2007-12-11
> **Thrasyllus said:**
> any file I create gets timestamped in BST. How can I stop this madness?

Late reply, but here goes:

The ext3 filesystem stores file timestamps in UTC.  The *ls* and *stat* commands convert to local time according to *${TZ}*.  So you should be safe.

The only bad news is if you have FAT32 filesystems (including memory sticks), and you'd have to check NTFS (anyone?).

---

### Post by matthewcraig on 2007-12-11
Mind using the "Thread Tools" menu at the top and marking this thread Solved ?  Thx

---

### Post by Wongkg on 2007-12-17
How does one invoke tzconfig? I mean, can I get the entire command for it? :) 

Thanks

---

### Post by odiseo77 on 2007-12-17
> **Wongkg said:**
> How does one invoke tzconfig? I mean, can I get the entire command for it? :) 

Thanks

I think tzconfig is not in Gutsy anymore (I couldn't even find it in the repositories; maybe it's obsolete?). Try with:

```
sudo dpkg-reconfigure tzdata
```

---

### Post by hatchetman82 on 2008-04-26
i couldnt find the "use UTC" setting in 8.04

---

### Post by mssever on 2008-04-27
In Hardy, start gconf-editor and set /apps/panel/applets/clock_screen0/prefs/gmt_time.

---


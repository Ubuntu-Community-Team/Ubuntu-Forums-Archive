---
title: "[SOLVED] CPU usage"
date: 2008-01-23
forum: General Help
---

### Post by Bruce M. on 2008-01-23
Hi folks,

I have a question about CPU usage.
In the image below there are:

**Left:** Conky showing 9 programs running in each of: **1** top_mem cpu, **2** top cpu and **3** top_mem mem
**Center:** My main conky file with all $execi commands removed

There is absolutely nothing else running, and the CPU usage is sitting at 27%. Just so you know, turning off the left conky made no noticable difference.

**Right:** At this time I put my conkymain back to its normal state, with my **System Temps** (1 $execi call every 10 seconds), and my **main weather** portion, from *Weather* down to *Moon*, 1 $execi call every 10 minutes, and then the **5 Day Forecast** with 2 $execi calls every 4 hours.  The CPU usage climbed to 30%, OK, I can live with that 3% increase, considering the 4 $execi calls

Because of another post I created, [Trimming Processes]("http://ubuntuforums.org/showthread.php?t=667499"), I managed to drop my average processes from 114 down to between 89 and 97-98, and rarely at 101, never higher of late.

**So my question is:**
Any ideas as to what is keeping my CPU usage so high (27%) when the computer is running idle?  *ie: I'm not running anything.* I've seen in the conky forums where some people have a CPU usage of 3-4%. I'd settle for 10% here.

Secondary question (after the fact):  What kind of CPU usage are the $execi calls using when they are in the process of waiting to do something?

[CENTER]
[[IMG]http://img222.imageshack.us/img222/82/screenshot1hj4.th.png[/IMG]](http://img222.imageshack.us/my.php?image=screenshot1hj4.png)
[/CENTER]

Thanks,
Bruce

---

### Post by Jimmey on 2008-01-28
Type "top" into a terminal. See what that says is eating your CPU cycles.

EDIT - Should have looked at the images before I posted. I think the fact is that you have a relatively slow processor. Also, how often does Conky update itself? What have you set the interval to?

---

### Post by Bruce M. on 2008-01-28
> **Jimmey said:**
> Type "top" into a terminal. See what that says is eating your CPU cycles.

EDIT - Should have looked at the images before I posted. I think the fact is that you have a relatively slow processor. Also, how often does Conky update itself? What have you set the interval to?

I did the test with conky running to show results.  But if I turn conky off, and let my machine sit idle for a few hours, then turn it back on I see that my "Down" has gone up by about 2MB.

I'm thinking that my ISP is "pinging" my cablemodem or some such thing.
In W2K I could "disconnect/reconnect" the ethernet card, but I can't do that with Ubuntu.

---

### Post by smac4president on 2008-01-30
Again try running top in a terminal and see if conky itself isn't the problem.  It looks like you have a lot of things with bright colors and all, and as the conky site says:

> Conky is generally very good on resources. However, certain objects in Conky are harder on resources then others. In particular, the $tail, $top, $font, and $graph objects are quite costly in comparison to the rest of Conky.

As Jimmy noted, you do have a relatively slow processor, which could be compounding the problem.

---

### Post by Bruce M. on 2008-01-30
> **Jimmey said:**
> Type "top" into a terminal. See what that says is eating your CPU cycles.

EDIT - Should have looked at the images before I posted. I think the fact is that you have a relatively slow processor. Also, how often does Conky update itself? What have you set the interval to?

*I apologize: Conky is chewing up "top" like crazy.*
The main portion of conky regenerates every second because of the time (with seconds)
Going to drop seconds and run at 60

The main Wearher portion every 10 min <-- changing to 30 min
and the 5 day forcast every 4 hours

I use:
default_color white
if I used the codes:
color 1 cyan
color 2 yellow
color 3 orange

Is it the sane as ${color orange}text$color

My brain is saying: Yes,dummy!
In a test I stripped ALL color out (except default) and CPU dropped to 10-12%

Guess I need some sacrifices here, what's worth what!

Thanks
Bruce

---

### Post by Bruce M. on 2008-01-30
> **smac4president said:**
> Again try running top in a terminal and see if conky itself isn't the problem.  It looks like you have a lot of things with bright colors and all, and as the conky site says:



As Jimmy noted, you do have a relatively slow processor, which could be compounding the problem.

They should add $color to that too.  I stripped color out to test with just default (white) CPU dropped to 11-12% .... 
Like I said above, now I decide what to sacrifice.  Probably will run with 2 colors only.

HEY!  Just noticed:  CPU: 9% because I changed the run time to 60 seconds, with FULL color.

Oh, time to play... Thanks you!
Bruce

---

### Post by Bruce M. on 2008-01-30
Changed Conky to:

update_interval 8.0

and watched CPU usage drop to [SIZE="4"]**4%**[/SIZE] when I'm not doing anything here.

Thanks Guys.
Bruce

---


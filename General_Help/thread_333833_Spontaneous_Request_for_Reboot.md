---
title: "Spontaneous Request for Reboot"
date: 2007-01-08
forum: General Help
---

### Post by ginandtonic on 2007-01-08
I've done a search of the threads and have not found this situation.  The problem I am having is that at random times, I lose control of my mouse, the CPU utilization spikes very high and then I get the shutdown screen showing the choices; restart, shutdown, hibernate, etc.  Attempts to cancel out of this screen always return to it so I have no choice but to restart.

I have been an Ubuntu user for about 3 weeks or so and this situation has only been happening for the past 4 days or so.  If I suspect any culprit it might be my installation of libglide3 but before I take it out, I wanted to find out if there were any methods that I could use to debug this problem.

Any assistance would be appreciated.

---

### Post by Jussi Kukkonen on 2007-01-08
Well, there should be something in the logs about something that weird...

When you get that condition again, try opening a virtual console (ctrl-alt-f1), logging in and checking some log files in /var/log/. ctrl-alt-f7 takes you back to X.

Some log files that could be helpful:
messages
Xorg.0.log
kern.log

---

### Post by ginandtonic on 2007-01-09
I was able to get a log from kern.log which seems to correspond to the problem.  Here is the log:

9 21:35:06 localhost kernel: [ 2847.870827] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.

It ended up not being a spontaneous reboot but when the mouse went crazy it apparently did some spurious clicks in the upper right hand corner of the page which is where the shutdown indicator is.

I've searched for this error and have seen it mentioned before but I could not really find a definitive way of fixing it.  Is there a fix for this?

---


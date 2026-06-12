---
title: "Using shutdown in a script started as a cron job?"
date: 2017-04-03
forum: General Help
---

### Post by BrianSwatton on 2017-04-03
Is it actually possible to use shutdown in a script activated as a cron job?  I can get the script to run from a crontab ok, the conditional tests work and files get written to, but the shutdown command doesn't execute, or give any error output when redirected to a file. I've used the shutdown command many times in terminal, so I believe I understand it. I'm using "shutdown -P +5". 

I've tried: 


[LIST]
[*]from both user and root crontabs. 
[*]including user or root in crontab before command path 
[*]changing permissions and owner of the called script to root. 
[*]with and without "sudo" in front of the shutdown command (I thought I shouldn't need sudo if running from root's crontab and root owning the script). 
[/LIST]

Am I flogging a dead horse?  Or should something here have worked, and maybe I've not hit the right combination of permissions/sudo etc. when I thought I had.

It's 12.04 by the way.  I'm not interested in upgrading, there are a number of machines working together here and I need them all the same. I spent many weeks trying to get a 16.04 (64b) to integrate into the system, but it fell at every hurdle.  Shame, as I thought it was great stand-alone, probably great with other 16.04 machines too.  12.04 has been brilliant anyway!

Thanks for reading.

Brian

---

### Post by bonestabone on 2017-04-03
Trying using the full path to the shutdown command, e.g. "/sbin/shutdown  -P +5". I've had these problems with the cron shell before, sometimes it can't find the right path.

---

### Post by BrianSwatton on 2017-04-03
Many thanks, I hadn't thought of that. 

I'll go and try that very shortly.  I'll report here.

---

### Post by BrianSwatton on 2017-04-03
Yes, that was it. 

Brilliant, it was driving me nuts. 

Thanks again.

---


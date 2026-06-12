---
title: "processes: how to know how they got started and why they are running"
date: 2015-10-01
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-10-01
Often I see odd things in lxtask and lxtask provides only minimal information. Like right now I have 2 conkys running. Experiments in the past showed me I can kill one of them (but which one?) and nothing bad happens. I have 6 instances of postgres (I thought that was for people running servers?). I have 2 xfstt, 2 lightdm (shouldn't that go away, once I've logged in graphically?), & 3 dbus-daemon. The other day I had a gazillion instances of "sh". Is there some way to find out exactly how a process got started, like "such and such a config file said to run such and such a script at time x"? And other that a general internet search and wikipedia, is there some way to find out whether there should be multiple instances or whether it should be there at all?

---

### Post by TheFu on 2015-10-01
**pstree**. [edited cmd name; had ptree]

If you are the only user of the box and don't know why all the sh processes are running, that is scary. Postgress is a DBMS. If you didn't install it, how did it get on the machine?

How to know which programs and who many instances should be running is learned by experience and by knowledge -  usually gained by reading  articles like those at wikipedia.

---

### Post by jwhitene on 2015-10-01
Check in /etc/init.d/  Anything in that directory is run when you boot up.  (Last time I checked anyways:))

Or you can check in the start up application 
[http://www.howtogeek.com/189995/how-to-manage-startup-applications-in-ubuntu-14.04/](http://www.howtogeek.com/189995/how-to-manage-startup-applications-in-ubuntu-14.04/)
see also
[http://stackoverflow.com/questions/7221757/run-automatically-program-on-startup-under-linux-ubuntu](http://stackoverflow.com/questions/7221757/run-automatically-program-on-startup-under-linux-ubuntu)

---

### Post by TheFu on 2015-10-01
> **jwhitene said:**
> Check in /etc/init.d/  Anything in that directory is run when you boot up.  (Last time I checked anyways:))

Actually, /etc/init.d/ is just "possible" things to run. It is a subtle difference. The actual items to run at startup will be linked into the /etc/rc#.d/ directories. Normally, the **update-rc.d** command is used to maintain those links. Upstart uses /etc/init/ and with systemd, there is a whole new way that I don't know yet.

Upstart and systemd are backwards compatible with the rc#.d/ method - which is part of  the historical "init" method in use for about 40 yrs now.

---

### Post by Dreamer Fithp Apprentice on 2015-10-01
Thanks, TheFu;
Thanks, JWhitnene.
> **TheFu said:**
> **ptree**.Neither "man ptree",  "sudo apt-get install ptree", or Synaptic indicate ptree as being in the repos. Is it the same as "pstree" or do I need to get it somewhere else? Pstree does look like it might be at least a start on what I'm after. Possibly after studying it I'll find it is a complete solution.
> **TheFu said:**
> If you are the only user of the boxI am.> **TheFu said:**
> and don't know why all the sh  processes are runningI don't. Yet.> **TheFu said:**
> that is scary.Well, shinola. You got me thinking re-install.

> **TheFu said:**
> Postgress is a DBMS. If you didn't  install it, how did it get on the machine?I certainly didn't install it for it's own sake. Possibly something I installed pulled it in as a dependency. Or following some instructions I installed it in route to getting something else to work. Or maybe en route to getting something to compile. I do sometimes play around with software still in an alpha state if it is a project I'm interested in. Sometimes those things aren't yet set up to pull in dependencies automatically. Could be. But I just purged it and it didn't warn about taking something else with it. This gives me some ideas about where to look to see if I might have installed it to support something else. So far, purging it didn't seem to break anything.

Thanks, JWhitene, for the links. I seem to spend a lot of time at both of those sites. I'll study those.

And thank you both for the info re init.d, etc. I've got a bit to study here.

---

### Post by TheFu on 2015-10-01
pstree - you are correct. Sorry.

---

### Post by vasa1 on 2015-10-03
> **Dreamer Fithp Apprentice said:**
> Often I see odd things in lxtask and lxtask provides only minimal information. Like right now I have 2 conkys running. Experiments in the past showed me I can kill one of them (but which one?) and nothing bad happens. I have 6 instances of postgres (I thought that was for people running servers?). I have 2 xfstt, 2 lightdm (shouldn't that go away, once I've logged in graphically?), & 3 dbus-daemon. The other day I had a gazillion instances of "sh". Is there some way to find out exactly how a process got started, like "such and such a config file said to run such and such a script at time x"? And other that a general internet search and wikipedia, is there some way to find out whether there should be multiple instances or whether it should be there at all?

Have you tried **ps** instead of **lxtask**? The information with **ps** can be quite informative. Depending on how curious I am, I (currently) like:```
ps -o pid,ppid,stime,time,command -H -u vasa1
```or```
ps -eHF
```
It would be nice to know how other users run **ps**.

---

### Post by TheFu on 2015-10-03
I generally use **top** or **htop**, but also have an alias from the early 1990s "psg" (ps with grep) - there is a program that does this today - ?**pgrep**? perhaps?

The "SEE ALSO" section of the ps manpage is handy for this stuff.

```
alias psg='ps -eaf | grep $*'
```
is the psg alias.  I didn't create it. Got it from someone in the IT lab where I worked back then.

---

### Post by vasa1 on 2015-10-03
I use **pgrep -a** [s]for[/s] to get the PID for specific apps and then pkill.

---

### Post by TheFu on 2015-10-03
> **vasa1 said:**
> I use **pgrep -a** for to get the PID for specific apps and then pkill.

If I need to kill a GUI app, **xkill**. There are lots of useful, old-school, X-apps still installed on Linux systems.

---

### Post by Dreamer Fithp Apprentice on 2015-10-23
Thank you, gents. I'll study all this.

---

### Post by Habitual on 2015-10-23
I use ```
lsof -p <pid_of_interest>
``` a lot to 'see' what started what.

---


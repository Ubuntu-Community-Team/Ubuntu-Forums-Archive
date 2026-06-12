---
title: "High Processor Usage - syslog - bash"
date: 2019-12-15
forum: General Help
---

### Post by djhampson on 2019-12-15
I have a Surface Pro 3 running Ubuntu 19.04 (GNU/Linux 5.0.10-surface-linux-surface x86_64). It is wall mounted running Home Assistant (from Home Automation) in Docker and Chrome running the Home Assistant web interface (so we can control lights, AC etc).

I have a recurring problem where my CPU usage goes from <5% to above 80% consistently. 

When I run sudo htop the top 4 processes are all from syslog with a command of -bash. 

[ATTACH=CONFIG]284615[/ATTACH]

I can kill any single one of the 4 processes via htop and all of them will disappear. The CPU load returns to normal for a period of time (can be minutes up to 2-3 hours) before the processes respawn and the CPU usage goes up again. 

I have tried to google these symptoms but have not been able to find anything relevant. 

Can anyone give me some tips as to what might be going on and how to diagnose?

---

### Post by djhampson on 2019-12-16
Link to screenshot in case it is too hard to read - [https://www.dropbox.com/s/7qa2x0d50mj82sq/2019_12_16%2011.32.38%20am.png?dl=0](https://www.dropbox.com/s/7qa2x0d50mj82sq/2019_12_16%2011.32.38%20am.png?dl=0)

---

### Post by dragonfly41 on 2019-12-16
[Stacer ]("https://github.com/oguzhaninan/Stacer")is a useful tool which might help in diagnostics.

---

### Post by djhampson on 2019-12-16
Thanks, I have installed that but wasn't able to identify anything specific.

I did try running a few of the cleanup tools but this has not fixed it.

Do you have any suggestions where or how I can use Stacer?

---

### Post by dragonfly41 on 2019-12-18
Admittedly Stacer only helps in visualising usage of resources and easily enabling/disabling resources.
You will need to conduct some more detective work to trace back erring processes (BASH?) to their source.

[Here is one approach I found]("https://askubuntu.com/questions/831513/how-to-see-detailed-information-about-a-given-pid").

Other approaches include analysing logs for keywords/strings.

---


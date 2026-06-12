---
title: "Simple python server with status of system?"
date: 2022-05-11
forum: General Help
---

### Post by josephchrzempiec on 2022-05-11
Hello, I'm trying to get a Simple python server setup with status of the server. Such as CPU, Memory, Hard drive . What's free and used network bandwidth. Honestly this is a little much for me. I'm not that much of a programmer at any means. But I did manage to get a simple Python server up and running from the help of youtube. Can someone help me please to come up with something?

edit: This is for locally online not to the internet.


Joseph

---

### Post by TheFu on 2022-05-11
What do you mean by "server"?  That's pretty vague.  Did you create a specialized client for the server too?

There are lots of existing solutions for this already. Is there a reason one of those cannot be used?  Check out munin [https://munin-monitoring.org/](https://munin-monitoring.org/) if you don't want to reinvent the wheel.  Or SysUsage [https://sysusage.darold.net/](https://sysusage.darold.net/) .  

I think **munin** is a little harder to get running because it can support hundreds of other systems reporting into it, building graphs for most things we need to know as admins.   [https://munin-monitoring.org/download/](https://munin-monitoring.org/download/) has 5 steps to looking at graphs for a fresh install.  The munin-node and munin server can be the same system ... or not.  They leave out more complex web server settings from their easy install which could be an issue for people not used to non-trivial web server configurations. 

**SysUsage** is simpler, based on my memory, but I haven't run it in about a decade.

---

### Post by josephchrzempiec on 2022-05-11
hello, I'm sorry let me rephrase that. I have ubuntu server OS setup with using SMB sharing. I just want to see locally everything on a webpage the status of the server. Such as Hard drives space, memory free/used, as well as network incoming and out going. Just the status of the system really. I'm only wanted to see it locally that's all in real time. on my monitor.

---

### Post by TheFu on 2022-05-12
It won't be a server if you want real-time data.  Typically, monitoring tools have to delay use by 1-5 minutes before they are graphed ... or useful.

If you want a desktop tool that gets close to real-time, check out Conky or Glances.  Ubuntu Server doesn't have any GUI, so those won't be too useful. I've never used either.

Conky [https://linuxconfig.org/ubuntu-20-04-system-monitoring-with-conky-widgets](https://linuxconfig.org/ubuntu-20-04-system-monitoring-with-conky-widgets)
Glances [https://www.tecmint.com/glances-an-advanced-real-time-system-monitoring-tool-for-linux/](https://www.tecmint.com/glances-an-advanced-real-time-system-monitoring-tool-for-linux/)

IMHO, without charting for days, weeks, months, these tools aren't so useful.  Seeing instantaneous values doesn't convey the same information for utilization that daily graphs with minute-by-minute changes shows.  Charts are what enterprises use to proactively upgrade hardware BEFORE it is needed, so their businesses keep running well.

---


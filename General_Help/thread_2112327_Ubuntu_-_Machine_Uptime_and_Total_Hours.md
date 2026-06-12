---
title: "Ubuntu - Machine Uptime and Total Hours"
date: 2013-02-04
forum: General Help
---

### Post by Tristan Tonks on 2013-02-04
Hi Guys,

I need to know what hours my machine has been running. I'm assuming that there is some register of when the machine has been 'on' - if so can I get a report of maybe date/time it was running?

Hope you can help any suggestions will be willingly tried.:)

---

### Post by stinkeye on 2013-02-04
Terminal...
```
uptime
```
Also have a look at **uptimed** and **uprecords-cgi**
> The uptime daemon tracks a system's highest uptimes via boot IDs,
using the system boot time to keep sessions apart from each other.
It features a console program to display statistics, and can
send mail if a milestone or a new record is reached.


Also have a look at the **last** command.
eg
```
last reboot
```
For older records try...
```
last reboot -f /var/log/wtmp.1
```

---

### Post by Tristan Tonks on 2013-02-05
Thank you - this is good info.

However; I should establish what I am trying to understand. (I should have done this more clearly in the first place :(  )

I am trying to get an idea of how much energy my machine has used over the last month. Uptime is giving me information that includes standby time when energy consumption is at a minimum.

If my machine has a combined load of 100W I need to know that it has been 'Working' for 'x' hours.

Is this possible?

---

### Post by Cheesemill on 2013-02-05
The only way to get an accurate measurement of power consumption is to plug it into a device that measures electricity usage.

Just knowing the uptime of your machine won't help as the computer will use varying amounts of power depending on what it's doing.

How are you calculating the load of your machine?

---

### Post by Tristan Tonks on 2013-02-05
You are correct of course, however it will give me an indicative power usage which is all I need right now. I am planning to connect something like [https://energyathome.googlecode.com/hg/](https://energyathome.googlecode.com/hg/) this in time but I have other projects running at the moment.
I would be using the rated power of my combined system so ((Watts X Hrs)/ capacity factor of say 80%) - thus giving a ballpark energy consumption for the system.

---


---
title: "Looking for a System Resource monitor"
date: 2008-01-19
forum: General Help
---

### Post by Helios38 on 2008-01-19
Hello,

I've been hunting for a System resource monitor

one that will keep itself integrated on my taskbar or maybe one that stays on the desktop.


Any Suggestions?


Thanks.

---

### Post by jleaker01z on 2008-01-19
System Monitor, located at System>Administration>System Monitor

If you want it on all the time you can fix it so it comes on at startup by going to System>Preferences>Sessions.  Under the Startup Programs tab, click 'new' , for name enter System Monitor, and the command is gnome-system-monitor.

---

### Post by eolson on 2008-01-19
When I want to monitor mine,  I open a console,  issue a top command,  then resize it and stick it in the upper right corner of my monitor.  I like it a lot better then the one available as a gui.  Gives me more info, but not as pretty.  Doesn't take as much space either.

---

### Post by wolfen69 on 2008-01-19
you should be able to right click a taskbar and choose "add to panel", then add system monitor.

---

### Post by Helios38 on 2008-01-20
no i mean, like something that would stay active, would monitor my CPU and such, and it would stay on my desktop or in my task bar

---

### Post by benny bronx on 2008-01-20
The system monitor suggested by wolfen69 would stay in your task bar and actively monitor cpu, network, etc.  The two black boxes in my task bar monitor the cpu and network activity.

---

### Post by y-lee on 2008-01-20
[gDesklets]("http://www.gdesklets.de/") has several system monitor tools that stay on the desktop that may serve your purposes. I use 
[LIST]
[*]FTB-mem-gauge
[*]FTB-cpu-gauge
[*]FTB-net-gauge
[/LIST]

You check out my desktop and see what ya think. Also of interest is an article i found, [gDesklets - FTB look]("http://polarbeardk.blogspot.com/2006/11/gdesklets-ftb-look.html")

---

### Post by Helios38 on 2008-01-25
i do like the one y-lee uses. thanks!

---

### Post by y-lee on 2008-01-25
No problem, thought ya'd like some eye candy there. I have a similar setup in my windows system also. tho using different software of course. :) 

gDesklets are cool plenty of options. have fun :popcorn:

---

### Post by ubername on 2008-02-26
> **y-lee said:**
> No problem, thought ya'd like some eye candy there. I have a similar setup in my windows system also. tho using different software of course. :) 

gDesklets are cool plenty of options. have fun :popcorn:

I have downloaded gdesklets and there are only 4 desklets available: a game (15 pieces), a quote-a-day,  a clock and a calendar:

Have I missed something?

---

### Post by ubername on 2008-02-26
The reason I am posting here is that 'System Monitor' says I am using c. 430 MB of my 3.0 GB RAM and 34 MB of my 500 MB swap.

I used the 'top command and found it reported 
top - 19:31:50 up 1 day,  3:44,  3 users,  load average: 0.13, 0.14, 0.21
Tasks: 140 total,   1 running, 139 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.2%us,  8.8%sy,  0.0%ni, 82.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3114624k total,  2835048k used,   279576k free,    54916k buffers
Swap:   498004k total,    34760k used,   463244k free,  2335396k cached


so I guess the default GUI system monitor is measuring something else?

Any clues?

---

### Post by y-lee on 2008-02-26
> I have downloaded gdesklets and there are only 4 desklets available: a game (15 pieces), a quote-a-day, a clock and a calendar:

Have I missed something?

How did you install gdesklets, in synaptic or apt? Or did you download it from somewhere else?

You should have also installed gdesklets-data, which includes alot of gdesklets applets :)

I also think more can be found online tho I not sure without googling. 

```
sudo aptitude install gdesklets-data
```

---

### Post by y-lee on 2008-02-26
> **ubername said:**
> The reason I am posting here is that 'System Monitor' says I am using c. 430 MB of my 3.0 GB RAM and 34 MB of my 500 MB swap.

top -  ...

Mem:   3114624k total,  2835048k used,   279576k free,    54916k buffers
Swap:   498004k total,    34760k used,   463244k free,  2335396k cached


so I guess the default GUI system monitor is measuring something else?

Any clues?

Honestly I never compared the two and it confused me at first but a little research revealed:


For top the Mem used line shows how much memory is used including cache, so the result in my case is  close to the amount of RAM installed on my machine. For a more accurate view of memory usage:

```
free -m
```

 and notice the line with  **+/- buffers&cache** is about the same as what the system monitor shows.

BYW the system monitor applet in gdesklets  I use shows the same info as gnomes system monitor :)

---

### Post by ubername on 2008-02-26
> **y-lee said:**
> How did you install gdesklets, in synaptic or apt? Or did you download it from somewhere else?

You should have also installed gdesklets-data, which includes alot of gdesklets applets :)

I also think more can be found online tho I not sure without googling. 

```
sudo aptitude install gdesklets-data
```

I installed it from the deb at the gkdesklets site (gdesklets_0.36-0ubuntu_i386.deb)

I am now downloading the desklets data you recommend, it has downgraded my version of desklets. I will let you know how I get on.

---


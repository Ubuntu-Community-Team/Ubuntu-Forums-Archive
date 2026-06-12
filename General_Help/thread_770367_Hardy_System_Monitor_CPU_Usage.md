---
title: "Hardy: System Monitor CPU Usage"
date: 2008-04-27
forum: General Help
---

### Post by svaens on 2008-04-27
Hi all, 

Just noticed something (after chasing down another problem). 

System Monitor on my installation takes lots of CPU. 

Before I start it (as reported by the little panel applet) usage is around 20%. Running System->Administration->System Monitor, pushes it up to around 90-100%. Close This particular app, and I watch the cpu usage level back down at around 20%

HOWEVER!! 

If I run system monitor using the Hardy Live CD, I can watch the CPU Usage sit at around 30%, I even tested this while playing an MP3. CPU didn't rise above 30% 

What could be installed to cause the system monitor act so nasty!?

---

### Post by svaens on 2008-04-27
UPDATE!!!!

I just read in one of the bug reports, that there is some sort of problem with the system monitor graphs... 
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)
It seems to update much faster than configured, and so if configured to every 1 seconds, it is faster, 
configure it to every 3 seconds, and my CPU usage whilst looking at the CPU History goes from 80% or so to 30%. 

This still doesn't solve my sound problem though... 
That my system seems to take so much CPU in doing simple X operations hints though at maybe an xconfig  problem rather than an actual sound problem (and sound was only a symptom) although, I do not experience much of a video or graphics problem...

---

### Post by ghost_ryder35 on 2008-04-27
next time this happens go to the terminal and issue
```

top

```
then screen shot it or copy the text onto this forum. It will let us know why the cpu is lagging
 
if you belive it is a xconfig problem run
 
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Nemisis215 on 2009-04-22
Hi Peeps

I was getting this problem also but in a much more extreme case i believe, when i opened m system monitor it sent both CPU's into 100% for about 5 seconds then went back down to 50% i changed the graph refresh time to 10 seconds and now it never goes above 5% on each CPU

Problem solved i believe :):)

---

### Post by Godly on 2009-04-22
> **Nemisis215 said:**
> Hi Peeps

I was getting this problem also but in a much more extreme case i believe, when i opened m system monitor it sent both CPU's into 100% for about 5 seconds then went back down to 50% i changed the graph refresh time to 10 seconds and now it never goes above 5% on each CPU

Problem solved i believe :):)

Where can this be changed?

---


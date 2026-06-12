---
title: "Configuring Conky For A Quad Core System"
date: 2012-10-14
forum: General Help
---

### Post by coljohnhannibalsmith on 2012-10-14
Hello,

I'm currently in the process of configuring conky for a quad core system.  I currently have a Dell 5520 with an I7 core.

The lines of code I'm having trouble with are the following:

${color yellow}Core 0: ${hr 2}$color
Freq: ${freq 1}MHz
${cpubar cpu1 10,70}
${cpugraph cpu1 000000 ffffff}

${color red}Core 1: ${hr 2}$color
Freq: ${freq 2}MHz
${cpubar cpu2 10,70}
${cpugraph cpu2 000000 ffffff}

I get the frequency on cores 0 and 1; but the rest of the code just draws nearly empty graphs.  The graphs show some activity; but it's so minimal it barely displays.  I'm also thinking about setting up all four cores as follows:

${color yellow}Core 0: ${hr 2}$color
Freq: ${freq 1}MHz
${cpubar cpu1 10,70}
${cpugraph cpu1 000000 ffffff}

${color red}Core 1: ${hr 2}$color
Freq: ${freq 2}MHz
${cpubar cpu2 10,70}
${cpugraph cpu2 000000 ffffff}

${color yellow}Core 2: ${hr 2}$color
Freq: ${freq 3}MHz
${cpubar cpu3 10,70}
${cpugraph cpu3 000000 ffffff}

${color red}Core 3: ${hr 2}$color
Freq: ${freq 4}MHz
${cpubar cpu4 10,70}
${cpugraph cpu4 000000 ffffff}

Can conky even handle 4 cores? 



Thanks Hannibal

---

### Post by wildmanne39 on 2012-10-14
Hi, yes conky can handle 4 cores, but you have to add 2 extra lines of code and change the core of the extra 2 lines to read 3 on one and 4 on the other but I am getting ready for work and it is a long process to get conky to work the way you want it too so hopefully someone else will jump in here.
Thanks

---

### Post by coljohnhannibalsmith on 2012-10-16
Bump...

BTW, I notice more activity on the graphs (they look almost normal) when the fan starts up on my laptop; but I'm finding it hard to believe that the graphs show almost no activity until the laptop starts getting hot.

---

### Post by QIII on 2012-10-16
The cpugraph shows the load on the cores.  At idle, that should be minimal.  Depending on the vertical scale of the graph, the line may simply not reach high enough to capture an entire pixel.

When your core load picks up, the graph becomes visible.  Your CPU also heats up, causing the fan speed to be adjusted.  The graph activity and fan increase are causally related to CPU load and only coincidentally related to each other.

---

### Post by coljohnhannibalsmith on 2012-10-16
> **QIII said:**
> The cpugraph shows the load on the cores.  At idle, that should be minimal.  Depending on the vertical scale of the graph, the line may simply not reach high enough to capture an entire pixel.

When your core load picks up, the graph becomes visible.  Your CPU also heats up, causing the fan speed to be adjusted.  The graph activity and fan increase are causally related to CPU load and only coincidentally related to each other.

Does that mean I already have this setup up correctly, or is there something else I need to do to get the graphs to register activity at normal load levels?

Thanks Hannibal

---

### Post by QIII on 2012-10-16
At idle you may not see anything if the vertical scale is small.  That is normal.  With an i7 I would expect you load percentage to be very low at idle.

Start any program and see if you get a transient spike.  Watch a Flash video and see if you get a sustained readout.

---

### Post by coljohnhannibalsmith on 2012-10-19
I got a transient spike on all 4 cores when starting Vuze, but it was small.

I'm going to try watching a flash video next.

---

### Post by QIII on 2012-10-19
A better test, now that I think about it would be to install pi
```
sudo apt-get install pi
```

and then open four terminals and run
```
pi 200000000
```

That should drive your cores to max and be pretty obvious.  But beware your cooling hardware and mind your core temps.

---


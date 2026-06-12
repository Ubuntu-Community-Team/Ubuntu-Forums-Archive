---
title: "Core 2 Duo - doesnt utilise full CPU speed?"
date: 2007-01-15
forum: General Help
---

### Post by stormyuk on 2007-01-15
Hello,

Just noticed that if my CPU is not so active I get:

```
cat cpuinfo
```

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4616.46

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4612.78
```

If I then run say:

```
fgl_glxgears
```

I get:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2394.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4616.46

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4612.78
```

Why is it only stressing one of the Cores? I would have thought it would push both to maximum?

Any ideas?

Cheers,

Mike

---

### Post by Ramses de Norre on 2007-01-15
A shot in the dark: what happens if you run two instances of fgl_glxgears?

---

### Post by stormyuk on 2007-01-15
I'll try that now. Out of interest with one fgl_glxgears output from "top"

```

top - 22:17:18 up  1:16,  1 user,  load average: 0.98, 0.72, 0.52
Tasks: 111 total,   2 running, 108 sleeping,   0 stopped,   1 zombie
Cpu(s): 49.8%us,  0.3%sy,  0.0%ni, 49.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035376k total,  1021728k used,    13648k free,     5972k buffers
Swap:  2096468k total,    17716k used,  2078752k free,   720512k cached
```

LOL bizarely with two instances running:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4616.46

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4612.78
```

and

```
top - 22:20:42 up  1:20,  1 user,  load average: 1.62, 1.06, 0.68
Tasks: 113 total,   5 running, 107 sleeping,   0 stopped,   1 zombie
Cpu(s): 54.7%us,  9.6%sy,  0.0%ni, 35.2%id,  0.0%wa,  0.3%hi,  0.2%si,  0.0%st
Mem:   1035376k total,  1016828k used,    18548k free,     6528k buffers

```

Whats going on?

](*,)

---

### Post by Rui Pais on 2007-01-15
> **stormyuk said:**
> Hello,

Just noticed that if my CPU is not so active I get:
...

If your cpu is not  very active why do you want it more active? are you cold ;)

it's your cpufreq-governor that must be "ondemand" or "conservative" so it will run lower when few things are required from it and will go to the maximum when it really needs (compilation , decompress files, intensive tasks... etc)

check with:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
```
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

---

### Post by stormyuk on 2007-01-15
> **Rui Pais said:**
> If your cpu is not  very active why do you want it more active? are you cold ;)

it's your cpufreq-governor that must be "ondemand" or "conservative" so it will run lower when few things are required from it and will go to the maximum when it really needs (compilation , decompress files, intensive tasks... etc)

check with:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
```
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

Its set for ondemand but surely fgl_glxgears should push it to full load, I was just curious why I cant seem to get my CPU pushing its maximum load. I dont want to run it at full load all the time but I would expect fgl_glxgears to load it full. :)

Is there an application I can run to force it to full load briefly, to satisfy my curious mind that it will do it, when its needed?

Cheers,

Mike

---

### Post by Ramses de Norre on 2007-01-15
Have you waited a few seconds before looking at cpuinfo? It sometimes takes a few seconds here for my cpu to get to a higher frequency.

---

### Post by stormyuk on 2007-01-15
Yes, although top never seems to report more than 50% load.

---

### Post by Rui Pais on 2007-01-15
but your log says it's run full...

> **stormyuk said:**
> 

```
fgl_glxgears
```

I get:

[CODE]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2394.000


since its a dual core it use one (usually the first) to do the heavy task

---

### Post by stormyuk on 2007-01-15
But only one core? Will Ubuntu not utilise both cores at the same time when its under heavy load? Or would I have to force one instance of gears to run on each core? (if its even possible?)

---

### Post by Rui Pais on 2007-01-15
That's probabily because it don't feel the need for activate the 2nd to the maximum.
it was a program running a simple proccess continuously. If you try 2 program with heavy use or something that do real paralel process they both go to maximum.

If you want to ensure that they are alive and well anc can work at most speed try load: 
```
 sudo modprobe cpufreq_performance
```

or use cpufreq-set to set both at maximum

---

### Post by stormyuk on 2007-01-15
Thanks, I dont really want to force them to maximum continously. :)

If I did the modprobe comand to test, how would I get it back in ondemand as it is now?

Cheers,

Mike

---

### Post by Rui Pais on 2007-01-15
Yes, you only need to unload the modules when you don't want it anymore.

An easy way would be do:
```
sudo cpufreq-set -c 0 -f 2.4G
sudo cpufreq-set -c 1 -f 2.4G
```

and check:
```
sudo cpufreq-info
```

(you may need to install the package cpufrequtils, a very useful one anyway...)

---

### Post by stormyuk on 2007-01-15
Ahh I worked that cpufrequtils out, thanks very much !

Mike

---

### Post by Seq on 2007-01-15
The issue is that a dual core machine has two cores. If you run a one single threaded application, it will stress one of the cores.


First of all, run the `gnome-system-monitor` to get some relatively real-time feedback with detail for both cpus. On my system they both graph with the same colour, so you may wish to change that.

Try running this in a terminal:
```
cat /dev/urandom > /dev/null
```

Notice that one core jumped to 100% utilization. It will also be running at full clock speed. Now open another terminal and do the same as above (while doing this, note how responsive your system still is ;)

You will now see the second core jump to 100% utilization.

If you keep tabs on it, you will see all sorts of fun things such as the cores alternatively jumping to 100% during system updates, etc.

---

### Post by Rui Pais on 2007-01-15
> **stormyuk said:**
> Sorry, I am a bit of a newbie at this. I can understand both of those comands and installed the cpu utils with adept.

However, what command do I use to put the CPU cores back in ondemand mode and not forced as above?

Cheers,

Mike

No prob:
```
sudo cpufreq-set -c 0 -g ondemand
sudo cpufreq-set -c 1 -g ondemand
```
;)

---

### Post by stormyuk on 2007-01-15
> **Seq said:**
> The issue is that a dual core machine has two cores. If you run a one single threaded application, it will stress one of the cores.


First of all, run the `gnome-system-monitor` to get some relatively real-time feedback with detail for both cpus. On my system they both graph with the same colour, so you may wish to change that.



Can I do this in KDE? 

Thanks,

Mike

(Thanks again Rui)

---

### Post by ~LoKe on 2007-01-15
A single application will run on a single core.  The point of dual core is to split the workload across both cores, but each should be doing completely different tasks.  There are of course some applications that will force an application to run on each core (eg. boinc/S@H).

From what I can see, your processor is doing exactly what it should be doing.

---

### Post by stormyuk on 2007-01-15
Yeh, sorry I am a newbie but its nice to be able to check and look at all this stuff, very refreshing from a Windows XP user. :)

Anyway, its time for bed. Work in the morning.

Thanks again everyone.

Mike

PS: I would still be interested to know if there is a KDE equivalent to `gnome-system-monitor`.

---

### Post by Rui Pais on 2007-01-15
yes, of course, stormyuk.


The sweet, sweet part it is was as **seq** point it out the way the system still keep responsive. It's purely amazing. 
My pentium4 fry last week, and i got this new duo2core and i'm still get used to it...

First time i used i was disappointed, cause it feels practically the same speed as the old P4, 3.2Gh. 
When i saw the cpuinfo i almost fall of the chair, though the same as you. In fact the speed ondemand it was so low i thought the cpu was broken :lol: 
Take me some hours until i understand that it's hard to make the box slow with this processors. And i try hard.
Today i spend the afternoon running folding protein simulation apps (things that run for 1 or 2 hours in 101% cpus), something that almost paralyze my old box and now, boy i managed to run 2 at same time, my wife logged in here from a terminal box running firefox and checking mail, and i managed to keep working on Mathematica (with large matrices) without even feel it slow, only a much more noise then usual cause the fans worked a lot...

I never liked a computer so much as i got this cpu. :)


edit: there is a kde equivalent but i don't know the name. it's in kcontrol i think... or search the menus os system/admin area

---

### Post by Choad on 2007-01-15
edit: redundant

---

### Post by Seq on 2007-01-15
> **Rui Pais said:**
> yes, of course, stormyuk.


The sweet, sweet part it is was as **seq** point it out the way the system still keep responsive. It's purely amazing. 
My pentium4 fry last week, and i got this new duo2core and i'm still get used to it...

First time i used i was disappointed, cause it feels practically the same speed as the old P4, 3.2Gh. 
When i saw the cpuinfo i almost fall of the chair, though the same as you. In fact the speed ondemand it was so low i thought the cpu was broken :lol: 
Take me some hours until i understand that it's hard to make the box slow with this processors. And i try hard.
Today i spend the afternoon running folding protein simulation apps (things that run for 1 or 2 hours in 101% cpus), something that almost paralyze my old box and now, boy i managed to run 2 at same time, my wife logged in here from a terminal box running firefox and checking mail, and i managed to keep working on Mathematica (with large matrices) without even feel it slow, only a much more noise then usual cause the fans worked a lot...

I never liked a computer so much as i got this cpu. :)


edit: there is a kde equivalent but i don't know the name. it's in kcontrol i think... or search the menus os system/admin areaI have a Core Duo laptop, and when both cores actually clock at full speed I know something is wrong (beagle indexing .jar files....)

As for KDE, there most definitely will be, but as I am not a KDE user I can not point you in the right direction. Sorry.

---


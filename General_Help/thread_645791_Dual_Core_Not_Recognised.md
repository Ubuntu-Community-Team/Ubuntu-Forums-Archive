---
title: "Dual Core Not Recognised"
date: 2007-12-20
forum: General Help
---

### Post by GravutyGuy on 2007-12-20
I was previously running 7.04 on my old laptop and it showed up both cores fine. i have recently bought a new dell desktop and installed Gutsy. The problem is, it only shows that there is 1 CPU in my system when in fact it is dual core and should therefore show 2

~$ ls /sys/devices/system/cpu/
cpu0  sched_mc_power_savings

~$ cat /proc/*cpu*
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 1000.000
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 2010.99
clflush size    : 64

I want to try and figure out why it is not showing as dual core and hopefully fix it so that it does. Another problem i have noticed is that even though this machine is supposedly 2 times faster than my last, it only works at around the same speed as my laptop. is there any reason for this? If so, is there a way to make it run at the speed it should be running at?

Thanks in advance to anyone that takes time to answer me.

Regards
Mikey

---

### Post by ~LoKe on 2007-12-20
Looks like you've messed around in the BIOS.  It's only showing up as 1GHz when it should be 2.8GHz.

---

### Post by GravutyGuy on 2007-12-20
I haven't touched the bios so it can't be that. Something is wrong though and i don't know how to fix it. Anyone got any ideas?

Mikey

---

### Post by Linteg on 2007-12-20
I'd say the clock frequency is due to cpufreq governors (frequency scaling), so that's nothing to worry about, that doesn't really help you here though... Which kernel are you running? Are you using any special boot-parameters (such as acpi=off)?

---

### Post by GravutyGuy on 2007-12-20
I don't have a clue which kernal i'm running - whatever came on the dvd inside 'Linux Format' magazine. I just installed it and have done nothing to it since,

Not even sure what boot parameters are to be honest so i doubt i'm running any 'special' ones.

I do know though that it's very annoying having a pc thats supposed to be running just under 6ghz and is actually only running at 1ghz. I dont want to reinstall vista but if thats the only way i'm going to get a fully functional machine then ill have no choice.

Why aren't these things simple!! lol

Mikey

---

### Post by ~LoKe on 2007-12-20
Type this into the terminal:
> uname -r
What's the output?

---

### Post by GravutyGuy on 2007-12-21
2.6.22-14-generic

I'm assuming that's the kernal?

I checked the bios a minute ago too and it shows that the cpu is running at 2800mhz.

Mikey

---

### Post by GravutyGuy on 2007-12-21
Bump?

---

### Post by Joeb454 on 2007-12-21
Well dual-core processors are actually a single processor. So that could be why it's only showing a single processor, though I'm not sure why it's only showing the speed as 1Ghz

---

### Post by GravutyGuy on 2007-12-21
I do think it's strange that it's only showing 1000mhz. Like i said, i checked the bios and that shows it running at the speed it should do.

I do know i don't want to have my machine running at 1ghz though as that is even worse than my laptop.

Short of reinstalling windows, i dont know what to do.

Mikey

---

### Post by snkmad on 2007-12-21
```
~$ ls /sys/devices/system/cpu/
cpu0  cpu1  sched_mc_power_savings

~$ cat /proc/*cpu*
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.112
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips        : 4022.31
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.112
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips        : 4018.56
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

Something isnt right with your pc.
The system really is finding only one CPU core.

About the clock being 1Ghz, its probably due AMD Cool'n'Quiet being turned ON in Bios. Set that to OFF and it should be always at the maximum speed.  But note that if you are using a laptop, its good to have it clocked lower, saves battery, and when you start a more demanding app, the clock will rise all by itself.

---

### Post by GravutyGuy on 2007-12-21
Well the CoolnQuiet would certainly explain the low clock speed. I actually have a desktop now so i'll be changing that when i get home.

It still doesn't solve the mystery of dual core though. My bios definately shows there being '2' cpu's but Ubuntu can't see both. Therefore, there must be something wrong with ubuntu that makes it not capable of seeing both. If this is the case, there must be a way of fixing it so that it can see both??  Question is - what??

Mikey

---

### Post by roaldz on 2007-12-21
> **GravutyGuy said:**
> Well the CoolnQuiet would certainly explain the low clock speed. I actually have a desktop now so i'll be changing that when i get home.

It still doesn't solve the mystery of dual core though. My bios definately shows there being '2' cpu's but Ubuntu can't see both. Therefore, there must be something wrong with ubuntu that makes it not capable of seeing both. If this is the case, there must be a way of fixing it so that it can see both??  Question is - what??

Mikey

Have you tried updating your bios? Could help... The 1 Ghz. Is indeed frequency scaling. Don´t worry about that;)

---

### Post by GravutyGuy on 2007-12-21
Not sure what you mean by frequency scaling but i shall look it up.

Surely the bios wouldn't need updating as its a brand new machine (2 weeks) from dell??

Mikey

---

### Post by GravutyGuy on 2007-12-21
Could it be possible that it can't see both due to the fact that the 64 bit version ubuntu isn't installed?

Mikey

---

### Post by mellowd on 2007-12-21
> **GravutyGuy said:**
> Well the CoolnQuiet would certainly explain the low clock speed. I actually have a desktop now so i'll be changing that when i get home.

It still doesn't solve the mystery of dual core though. My bios definately shows there being '2' cpu's but Ubuntu can't see both. Therefore, there must be something wrong with ubuntu that makes it not capable of seeing both. If this is the case, there must be a way of fixing it so that it can see both??  Question is - what??

Mikey

It really doesn't need to be changed. The CPU will scale up to its top speed when it's needed and clock lower when it's not doing anything. It's silly to have the cpu running at 2.8GHz when all it's doing is rendering a web page. Best to leave it on.

---

### Post by mellowd on 2007-12-21
> **GravutyGuy said:**
> Could it be possible that it can't see both due to the fact that the 64 bit version ubuntu isn't installed?

Mikey

Nope, I'm running 32bit ubuntu with my amd X2 and I see both cores

---

### Post by GravutyGuy on 2007-12-21
Right, that makes sense. Just wish someone knew how to make my pc see both cores.

---

### Post by chewearn on 2007-12-21
1. By default, ubuntu set the cpu governor to "ondemand".  This will trottle down the frequency to lowest possible when no load.  If you use laptop, this should be preferred (save battery and a lot less heat)

I prefer my desktop to have full speed all the time, so I set the governor default to performance (though this mean the fan is running  a bit faster and noiser)


2. The AMD X2 should really show two processors (mine does).  Something is wrong here.  If you run this command:
```
uname -a
```
you should see "SMP" some where in the output.

---

### Post by GravutyGuy on 2007-12-21
I'll give it a try when i get home and let you know :-)

---

### Post by mellowd on 2007-12-21
You'll see something like this (this is on my AMD X2):

```
uname -a
Linux simba 2.6.22-14-server #1 SMP Sun Oct 14 23:34:23 GMT 2007 i686 GNU/Linux
```

---

### Post by jfank on 2007-12-21
I'm sorry I don't really have much of an answer for you, but I'm running the 32-bit version of Kubuntu, and I have the Intel Centrino Duo running at 1.86 Ghz.  It will only read it as one processor on my system, but it will clock it at the full speed when it has to.  I don't quite understand the whole thing with the duo core, but I have noticed with Linux it won't always show the processor as a dual core; that sometimes it will only show as a single core.  On my other computer that I have Open Suse running on it will show that core as a dual, and with my desktop that I have regular Ubuntu on it will also show that as a dual, but on my Sony laptop I'm running on right now it only shows the processor as a single core.  

I think you might want to consider running a game or something that will use that processor to it's fullest and then see what it reads then.  I hope someone else will have a full answer for you, and with that has been posted in here so far that it helps you to solve this issue.  On another note though, Linux doesn't require a fast processor to run, so you might never see it running at it's fullest.  Some people that run Linux might see their processor running at the fullest, but it depends on what you use your system for as well.

Once again I'm sorry I wasn't that big of a help here, but just wanted to give you my experience with the duo core processor.  Oh' besides my Sony the other 2 are Dell systems if that is any help with the duo core problem, but all 3 have the Intel I don't have a system yet that runs AMD.

---

### Post by Ptero-4 on 2007-12-21
It can be a defective processor (and yes, sometimes they come defective from the factory) or it can be that you need the SMP-enabled kernel.

---

### Post by chewearn on 2007-12-21
[quote=jfank;3991465]I'm sorry I don't really have much of an answer for you, but I'm running the 32-bit version of Kubuntu, and I have the Intel Centrino Duo running at 1.86 Ghz.  It will only read it as one processor on my system, but it will clock it at the full speed when it has to.  I don't quite understand the whole thing with the duo core, but I have noticed with Linux it won't always show the processor as a dual core; that sometimes it will only show as a single core.  On my other computer that I have Open Suse running on it will show that core as a dual, and with my desktop that I have regular Ubuntu on it will also show that as a dual, but on my Sony laptop I'm running on right now it only shows the processor as a single core.  

I think you might want to consider running a game or something that will use that processor to it's fullest and then see what it reads then.  I hope someone else will have a full answer for you, and with

Edit:
Eh?  What happened to my post?  Got corrupted [SIZE=1]*#-o*[/SIZE][SIZE=1]*#-o*[/SIZE][SIZE=1]*#-o*[/SIZE][SIZE=1]*#-o*[/SIZE][SIZE=1]*#-o*[/SIZE]

---

### Post by GravutyGuy on 2007-12-21
Here is the result of:

```
uname -a
```

```
Linux mikey-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

It does indeed say that it is the SMP kernal

Mikey

---

### Post by chewearn on 2007-12-21
> **GravutyGuy said:**
> Here is the result of:

```
uname -a
``````
Linux mikey-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```It does indeed say that it is the SMP kernal

Mikey

You might want to check your BIOS, see if there is a setting which disable multicores.  I believe Dell uses F2 key to acccess the BIOS during POST.

---

### Post by GravutyGuy on 2007-12-21
I've just started boinc and ran the "cat /proc/*cpu*" command and it gave exactly the same results as previous. Boinc is very cpu intensive so this really should have kickstarted something. Instead it still showed as running at 1000mhz.

Another strange thing i have found, when i click on system monitor and go to resources, it shows my cpu going at 100%, even though the processes only total about 10%. This happens with or without boinc running. I'm seriously starting to get annoyed with it now!!

Mikey

---

### Post by ~LoKe on 2007-12-21
Sounds to me like you've got a defective computer.  Boot up a different LiveCD, or install Windows (whichever you're most willing to do) and see what the result is.  Neither your processor or motherboard would be uncommon, so we know there's no compatibility issue here.

---

### Post by GravutyGuy on 2007-12-21
I've just gone back into the bios and disabled 'CoolnQuiet'

This is now the result for my pc:

```
~$ cat /proc/*cpu*
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 2812.836
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 5630.75
clflush size    : 64
```

It now at least shows the correct speed but still doesnt recognise 2 cores. There was no option in the bios for core useage.

I'll try running a live cd and see what results i get

Mikey

---

### Post by GravutyGuy on 2007-12-21
Well i'm currently running a live cd of gutsy (i still think these things are great) and low and behold, i have 2 cores!!! 

```
ubuntu@ubuntu:~$ cat /proc/*cpu*
```

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 2812.756
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips        : 5630.70
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping        : 3
cpu MHz         : 2812.756
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips        : 5625.49
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

Looks like i'll be doing a fresh install

Mikey

---

### Post by GravutyGuy on 2007-12-22
Well i installed the 64bit version of ubuntu and it recognises both cores now. Only problem is, boinc won't run on a 64bit machine. 

i made a live cd of the i386 version and ran it from the cd to find out if it would see both cores. It didn't!! 

Obviously it needs to be running the 64 bit version to see them both! 

Mikey

---

### Post by mellowd on 2007-12-22
> **GravutyGuy said:**
> Well i installed the 64bit version of ubuntu and it recognises both cores now. Only problem is, boinc won't run on a 64bit machine. 

i made a live cd of the i386 version and ran it from the cd to find out if it would see both cores. It didn't!! 

Obviously it needs to be running the 64 bit version to see them both! 

Mikey

It shouldn't. I'm running the 32bit version of server

---


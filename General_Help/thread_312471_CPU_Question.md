---
title: "CPU Question"
date: 2006-12-04
forum: General Help
---

### Post by benuski on 2006-12-04
Hey, I was just wondering if I was reading this output wrong, or if there is something wrong with my computer.  I typed in 
```
cat /proc/cpuinfo
```
into the terminal, and this is what I got out:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1400MHz
stepping        : 5
cpu MHz         : 600.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2
bogomips        : 1200.18

```
Now, it says that I have a 1.4 GHz chip, but then it says my CPU MHz is only 600.  Am I reading this wrong, or is that weird?

---

### Post by Ramses de Norre on 2006-12-04
Have you got cpu scaling turned on?

---

### Post by benuski on 2006-12-04
I don't believe so.  I haven't changed any settings to my CPU since installing.

---

### Post by nixclusive on 2006-12-04
CPU scaling is a process by which linux tries to save laptop battery by lowering the running CPU frequency. check out if you have powernowd running: ```
ps -e | grep powernowd
```

---

### Post by benuski on 2006-12-04
Nothing came up when I typed in 
```
ps -e | grep powernowd

```
So I assume I don't have it running...

---

### Post by benuski on 2006-12-04
Although, I ran powernowd, and it came up with this:

```
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 600Mhz - 1400Mhz (7 steps)

```

So how would I change it?  Or is there really any need to do so?

---

### Post by drphilngood on 2006-12-04
```
sudo chmod +s /usr/bin/cpufreq-selector
```

See this thread for more information:

[cpufreq scaling applet: manual scaling]("http://ubuntuforums.org/showthread.php?t=214007")

---

### Post by benuski on 2006-12-04
Thanks for all the help, guys!  Its working fine now

---


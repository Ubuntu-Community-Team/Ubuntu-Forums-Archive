---
title: "lpd using high cpu"
date: 2007-07-23
forum: General Help
---

### Post by IndigoMontoya on 2007-07-23
I am using an up to date feisty install and am having problems with lpd constantly using high cpu.

I have two networked printers installed (and they both are being printed to fine).  when I run top I get (sorted by cpu and cut off):

```
~$ top

top - 15:12:00 up  4:49,  5 users,  load average: 5.23, 3.90, 3.58
Tasks: 158 total,   6 running, 150 sleeping,   0 stopped,   2 zombie
Cpu(s):  7.7%us, 85.0%sy,  0.0%ni,  5.7%id,  0.7%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:   1034652k total,  1014316k used,    20336k free,    55044k buffers
Swap:  2144668k total,   722200k used,  1422468k free,    46156k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5489 daemon    25   0  505m 363m  680 R   47 36.0 118:35.28 lpd                
 5454 daemon    25   0  518m 310m  680 S   39 30.7  95:16.44 lpd                
 5444 daemon    25   0  4720  468  368 S    1  0.0   1:44.03 lpd                
 7659 spruce    15   0  342m  45m  11m S    1  4.5   7:26.98 Xgl                
 9024 daemon    25   0     0    0    0 R    1  0.0   0:00.02 lpd                
 8538 spruce    15   0  2320 1196  880 R    0  0.1   0:00.01 top                
    1 root      18   0  2912  512  460 S    0  0.0   0:01.38 init     
```

I have a dual core thinkpad t60.  Anybody have any thoughts?  When the computer boots it is fine, but the longer it goes (hours, not days) the less responsive it is.  a 'sudo killall lpd' fixes it

thanks

---

### Post by IndigoMontoya on 2007-07-30
does anybody have any ideas about this?  or even who else to ask?

---


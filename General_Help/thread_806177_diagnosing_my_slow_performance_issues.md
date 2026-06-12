---
title: "diagnosing my slow performance issues"
date: 2008-05-24
forum: General Help
---

### Post by evencoil on 2008-05-24
My Xubuntu installation is performing kind of sluggishly and I think its because somethings wrong since my CPU should have plenty of power for Xubuntu (2.7 Ghz Celeron with 1 GB RAM).

I realize this is a vague problem :)...so my specific question is, how can I go about diagnosing this so that I can start asking more specific questions?

---

### Post by |{urse on 2008-05-24
can you post the output of these commands?

top

smartctl -i /dev/sda

*if command not found then sudo apt-get install smartmontools

cat /proc/cpuinfo

hdparm -T /dev/sda

also what version of xubuntu did you install? Did you do updates?

and what model of hard drive you have would be helpful.

you should also look in your bios and disable "speedstep" if it is an option.

---

### Post by evencoil on 2008-05-24
top:

```

top - 18:04:46 up 58 min,  3 users,  load average: 1.32, 1.50, 1.50
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s): 47.3%us,  8.7%sy,  0.2%ni, 42.6%id,  1.0%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:   1027276k total,  1005004k used,    22272k free,   110724k buffers
Swap:  3004112k total,        0k used,  3004112k free,   338088k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 6890 evencoil  20   0  214m  93m  22m S 20.6  9.3  16:57.50 rhythmbox                                                                                       
 6587 root      20   0  246m  36m  12m S  5.6  3.7   5:29.61 Xorg                                                                                            
 6752 evencoil  20   0 39940  13m 7112 S  3.7  1.4   1:14.06 xfce4-mixer-plu                                                                                 
 7660 evencoil  20   0  2308 1120  852 S  3.7  0.1   0:03.54 top                                                                                             
 6753 evencoil  20   0 39892  14m 6700 S  1.9  1.4   1:02.41 xfce4-cpugraph-                                                                                 
 7514 evencoil  20   0  161m  72m  21m S  1.9  7.2   2:52.99 firefox-2-bin                                                                                   
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.58 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                                         
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kblockd/0                                                                                       
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  117 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
  151 root      20   0     0    0    0 S  0.0  0.0   0:00.18 pdflush                                                                                         
  152 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  153 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kswapd0                                                                                         
  193 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1467 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1471 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1501 root      15  -5     0    0    0 S  0.0  0.0   0:00.52 ata/0                                                                                           
 1509 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 1516 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 khpsbpkt                                                                                        
 1577 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 1579 root      15  -5     0    0    0 S  0.0  0.0   0:01.28 scsi_eh_1                                                                                       
 1980 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                     
 1992 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_1                                                                                     
 2501 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                       
 2517 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 kjournald                                                                                       
 2773 root      16  -4  2432  980  380 S  0.0  0.1   0:01.02 udevd                                                                                           
 3083 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                                                      
 4558 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4559 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4563 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4564 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4566 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4734 root      20   0  2456 1360  692 S  0.0  0.1   0:00.02 acpid                                                                                           
 4761 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                     
 4847 syslog    20   0  1936  648  512 S  0.0  0.1   0:00.08 syslogd                                                                                         
 4903 root      20   0  1872  536  444 S  0.0  0.1   0:00.06 dd                                                                                              
 4906 klog      20   0  3300 2116  424 S  0.0  0.2   0:00.22 klogd                                                                                           
 4928 messageb  20   0  2820 1248  796 S  0.0  0.1   0:01.60 dbus-daemon                                                                                     
 4945 root      20   0 12892 2024 1748 S  0.0  0.2   0:00.09 NetworkManager                                                                                  
 4958 root      20   0  3536 1320 1132 S  0.0  0.1   0:00.00 NetworkManagerD                                                                                 
 4972 root      20   0  4112 1116  908 S  0.0  0.1   0:00.00 system-tools-ba   
```

I'm putting /dev/sdb because I have 2 hard drives and sda is the one with my old windows 2000 install on it. 

smartctl -i /dev/sdb:

```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar family
Device Model:     WDC WD800BB-00CAA1
Serial Number:    WD-WMA8E1368410
Firmware Version: 17.07W17
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat May 24 18:08:38 2008 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

(oops I guess it was 2.4 Celeron...:oops:)
cat /proc/cpuinfo:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.40GHz
stepping        : 9
cpu MHz         : 2405.542
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid xtpr
bogomips        : 4815.75
clflush size    : 64


```

hdparm -T /dev/sdb:
```


/dev/sdb:
 Timing cached reads:   376 MB in  2.01 seconds = 186.71 MB/sec


```

I installed Ubuntu, then Kubuntu, and now I'm settled on Xubuntu. But I've done all this by adding, e.g. kubuntu-desktop through package manager, and I haven't removed Ubuntu and Kubuntu yet...

And this model is hard drive is a Western Digital 80GB EIDE, can't quite remember the exact specs but if its still important let me know and I'll look it up.

edit: (nm I see it says in the output of smartctl what it is)

---

### Post by |{urse on 2008-05-24
oh, I've seen serious sluggish performance after going from ubuntu-desktop to kubuntu-desktop and i've never tried going to xubuntu-desktop after all that lol. Your processor is recognized your processes look good and thats a decent hard disk. Might want to backup and try a fresh reload. Everything else looks healthy. BTW a 2.4ghz celeron performs about half as well as a 2.4ghz pentium equivalent If you are just now noticing a sudden performance decrease reinstalling would probably be your best bet. Was there a speedstep setting in your bios?


also do a 

smartctl -H /dev/sda

sorry forgot that

---

### Post by evencoil on 2008-05-24
there was no speedstep setting. And smartctl -H /dev/sda says passed. I can't quite remember, but I think I started seeing these performance issues after I installed Kubuntu over Ubuntu. And then I went to Xubuntu because I thought that would be faster. So maybe the issue is having multiple installs as you suggest...

---

### Post by |{urse on 2008-05-24
yeah (sorry went out to see a movie) sounds like you need a reload.

---

### Post by evencoil on 2008-05-27
the reload make a big difference; thanks!

---

### Post by |{urse on 2008-05-30
Awesomeness HI-FIVE 

:guitar:

---


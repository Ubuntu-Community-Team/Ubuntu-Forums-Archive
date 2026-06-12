---
title: "Slow PC after boot"
date: 2013-07-20
forum: General Help
---

### Post by Matths87 on 2013-07-20
Hello everybody, I haven't posted here for a while :)
I am currently using a Sony Vaio laptop (CPU: Intel Core i3, RAM: 4 GB, HDD: 750 GB) with Ubuntu 13.04 (64 bit version) installed on it. The system works pretty well, apart from the following issue: when I boot the computer and log in, the machine works extremely slowly for a couple of minutes. Subsequently the problem disappears and I am able to work at "full speed". This is more evident using Gnome 3 and less noticeable using KDE. My personal (and probably wrong) belief is that this is due to my encrypted /home partition, although my laptop should be fast enough to handle encryption...

To make you have an idea of the structure of my hard disk allocation:

```

root@mattia-SVE1511K1EW:/home/mattia# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 testine, 63 settori/tracce, 91201 cilindri, totale 1465149168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x8c126f2e

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    34353151    17175552   27  Hidden NTFS WinRE
/dev/sda2        34353152    35069951      358400    7  HPFS/NTFS/exFAT
/dev/sda3        35069952   455919615   210424832    7  HPFS/NTFS/exFAT
/dev/sda4       455921662  1465147391   504612865    5  Esteso
/dev/sda5       455921664   463927295     4002816   82  Linux swap / Solaris
/dev/sda6   *   463929344   522520575    29295616   83  Linux
/dev/sda7       522522624  1465147391   471312384   83  Linux

Disco /dev/mapper/cryptswap1: 4098 MB, 4098883584 byte
255 testine, 63 settori/tracce, 498 cilindri, totale 8005632 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xb06f9190

Il disco /dev/mapper/cryptswap1 non contiene una tabella delle partizioni valida

```

I am sorry for the Italian output, but I don't know how to set the shell produce English results... It should be anyway quite clear to you Ubuntu experts :D As you see, I am (quite regrettably) using Windows alongside Ubuntu!

 I would really appreciate any suggestions you may give me!

---

### Post by oldfred on 2013-07-20
Supposedly encryption only slows a system slightly.
Linux normally caches what your are doing in RAM so that does make it faster once you have loaded everything in RAM and only a new app then has to go back to hard drive to load data.

With 4GB of RAM you should not have any issues. I have 4GB and an older dual core system and it works well.
What video system do you have? Intel or an add in chip?

Minor point that is not related to issue. Windows has to have boot flag on the partition it uses to boot from, or to make repair, or install into. You need to move boot flag to sda2 (or sda3). Grub does not use boot flag and chainloads to Windows without it. But if you ever have to reinstall the Windows boot loader and boot, you need boot flag on correct partition. You also should make a Windows repairCD or flash from Windows, again just in case in the future.

---

### Post by Matths87 on 2013-07-20
> **oldfred said:**
> 
What video system do you have? Intel or an add in chip?


I have an Intel HD graphics 3000 :) Could this be related to my problem?

> **oldfred said:**
> 
Minor point that is not related to issue. Windows has to have boot flag on the partition it uses to boot from, or to make repair, or install into. You need to move boot flag to sda2 (or sda3). Grub does not use boot flag and chainloads to Windows without it. But if you ever have to reinstall the Windows boot loader and boot, you need boot flag on correct partition. You also should make a Windows repairCD or flash from Windows, again just in case in the future.


Thank you for pointing out this issue with my installation.

---

### Post by 2F4U on 2013-07-20
What is running in the background when you login? You can find out by using task manager, top or htop.

---

### Post by Matths87 on 2013-07-20
```

top - 17:48:26 up 2 min,  2 users,  load average: 3.61, 1.70, 0.65
Tasks: 185 total,   1 running, 182 sleeping,   0 stopped,   2 zombie
%Cpu(s):  0.8 us,  2.5 sy,  0.3 ni, 60.3 id, 36.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3946628 total,  1389204 used,  2557424 free,    95944 buffers
KiB Swap:  4002812 total,        0 used,  4002812 free,   841500 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                                                                  
 2249 mattia    20   0  314m  10m 4692 S   6.6  0.3   0:01.18 tracker-store                                                                            
 2613 mattia    20   0  695m  21m  14m S   4.3  0.6   0:01.05 gnome-terminal                                                                           
 1192 root      20   0  234m  30m  23m S   3.0  0.8   0:01.78 Xorg                                                                                     
 2224 mattia    20   0 1658m 111m  46m S   3.0  2.9   0:06.65 gnome-shell                                                                              
 2250 mattia    39  19  313m 8812 6140 D   2.7  0.2   0:00.44 tracker-miner-f                                                                          
 2182 mattia    20   0  891m  20m  14m D   1.0  0.5   0:00.25 gnome-settings-                                                                          
  232 root      20   0     0    0    0 S   0.7  0.0   0:00.36 kworker/u:5                                                                              
    3 root      20   0     0    0    0 S   0.3  0.0   0:00.07 ksoftirqd/0                                                                              
   10 root      20   0     0    0    0 S   0.3  0.0   0:00.37 rcu_sched                                                                                
    1 root      20   0 27252 3068 1452 S   0.0  0.1   0:01.11 init                                                                                     
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd                                                                                 
    4 root      20   0     0    0    0 S   0.0  0.0   0:00.12 kworker/0:0                                                                              
    5 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                             
    6 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/u:0                                                                              
    7 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/u:0H                                                                             
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0                                                                              
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcu_bh                                                                                   
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0                                                                               
   12 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/1                                                                               
   13 root      20   0     0    0    0 S   0.0  0.0   0:00.04 ksoftirqd/1                                                                              
   14 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/1                                                                              
   15 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/1:0                                                                              
   16 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/1:0H                                                                             
   17 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/2                                                                               
   18 root      20   0     0    0    0 S   0.0  0.0   0:00.15 ksoftirqd/2                                                                              
   19 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/2                                                                              
   20 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/2:0                                                                              
   21 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/2:0H                                                                             
   22 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/3                                                                               
   23 root      20   0     0    0    0 S   0.0  0.0   0:00.03 ksoftirqd/3                                                                              
   24 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/3                                                                              

```

I don't see anything strange here... Nevertheless, my laptop is very slow and the hard disk keeps on working without any apparent reason.

---

### Post by oldfred on 2013-07-20
I am not familiar with tracker-store, but it is using a lot of cpu?

[http://forums.opensuse.org/english/get-technical-help-here/applications/464686-solved-how-disable-tracker-store-processes-eat-100-cpu.html](http://forums.opensuse.org/english/get-technical-help-here/applications/464686-solved-how-disable-tracker-store-processes-eat-100-cpu.html)

---

### Post by Matths87 on 2013-07-20
I don't thinks so, it doesn't appear to use that much CPU time.

---

### Post by oldfred on 2013-07-20
But is that after you have been running a while or just after startup when things are slow.

---

### Post by Matths87 on 2013-07-20
What do you mean? If you are talking about the slowness, this one lasts a couple of minutes, depending on if I am using KDE or Gnome. On the other hand, if you are referring to the tracker-store process, it has now disappeared :)

---

### Post by 2F4U on 2013-07-20
If you look at the load average, you see 3.61. Assuming that your processor is dual core, that means your system has been overloaded, which may be the reason for the slowness after login:

[http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)

---

### Post by Matths87 on 2013-07-20
Ok, but is there a way to trace the reason of such overloading? :P

EDIT: my processor has a dual-core architecture, as you correctly guessed.

---

### Post by Matths87 on 2013-07-20
Looking carefully at the task manager straight after the boot, I realized that my issues are due to store-track. I consequently tried to disable it following oldfred's link, but after having rebooted this process is still with me... Any other idea on how disabling it?

---

### Post by 2F4U on 2013-07-20
It may be a service installed by an application or it may be something in the autostarted applications (these are executed after you login). The autostarted applications are something that run under your user, so you will be able to manage them. Regarding services, it may be helpful to use bootchart:

[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by 2F4U on 2013-07-20
My question would be why tracker is on your system, since it is not part of a default Ubuntu installation. Ubuntu uses zeitgeist. So, if you don't need it you could remove it.

[http://ubuntuforums.org/showthread.php?t=2113387](http://ubuntuforums.org/showthread.php?t=2113387)

---

### Post by Matths87 on 2013-07-20
```

sudo apt-get remove --purge tracker

```

solved my issue once and for all. I wonder how this messy package ended up being installed...
Thank you for your precious help :popcorn::)

---

### Post by silconsystem on 2013-07-20
Hi there,

You could be right about ur graphics card, mine burned out recently and I could no longer boot into Ubuntu 13.04, everything above 12.04 had issues. Have you tried changing your session to unity 2d yet?
Maybe you need some different drivers for your system. Try googling your card specs and ubuntu 13.04 and see if some similar issues come up !


Good luck,


Rob

---


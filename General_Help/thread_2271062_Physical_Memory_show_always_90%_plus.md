---
title: "Physical Memory show always 90% plus"
date: 2015-03-27
forum: General Help
---

### Post by bhavik2 on 2015-03-27
Currently i am using  Ubuntu 14.04.2 LTS.
Whenever i see using free -m command its show me very less amount of memory remains.

I am just a not using so many application still showing "Physical Memory show always 90% plus".
```

root@bhavik:/var/# free -m
             total       used       free     shared    buffers     cached
Mem:          3849       3642        206        273         16        634
-/+ buffers/cache:       2992        857
Swap:         7811       3300       4511

```

I have lenovo G50-70 laptop.
Can any one have idea this is related to hardware or Ubuntu ?

Please suggest me how to fix it.

---

### Post by TheFu on 2015-03-27
a) using an onboard GPU? It steals RAM for video use.
b) disk buffers.
c) Huge, memory sucking, web browsers

From the manpage:
>        free  displays the total amount of free and used physical and swap mem&#8208;
       ory in the system, as well as the buffers  used  by  the  kernel.   The
       shared  memory column represents either the MemShared value (2.4 series
       kernels) or the Shmem value (2.6 series kernels and later)  taken  from
       the  /proc/meminfo  file.  The  value is zero if none of the entries is
       exported by the kernel.

For example, one of my systems:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:         16040      14319       1720          1       3042       2550
-/+ buffers/cache:       8726       7313
Swap:        11632       2258       9374
```
And a netbook:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1936       1763        172         95         45        440
-/+ buffers/cache:       1277        658
Swap:         1987         13       1974
```
Notice the difference in buffer usage? The first machine runs multiple virtual machines and doesn't have any GUI code running. The 2nd is a 2G total RAM, with onboard Intel GPU. To see more details, other programs that monitor RAM use are needed. Start with top/htop.

See how nicely the columns line up with code tags?

---

### Post by v3.xx on 2015-03-27
How bout this

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by ajgreeny on 2015-03-27
The two most important lines in your output are ```
-/+ buffers/cache:       2992        857
Swap:         7811       3300       4511
```which actually shows that you have nearly a GB of ram free (the 857 figure), however, you have a lot of your swap in use which suggests either than you're doing something that is "ram intensive" in use or there is something else going on a leaking memory in some way.

What were you using when you ran that free -m command?  Any virtual machines running?

And don't forget that the top line of figures can be a bit confusing if you are not aware of the details shown in that linuxatemyram link above.

---

### Post by bhavik2 on 2015-03-30
Hi All,

 Thanks for the response.

There is no virtual muchine running.

Just plain Ubuntu with php installed .

This is my TOP command output.Currently its consume Physical Memory 

 97%

```

top - 16:40:12 up  5:09,  6 users,  load average: 0.33, 0.32, 0.44
Tasks: 246 total,   2 running, 244 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.5 us,  1.7 sy,  0.0 ni, 89.6 id,  1.3 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3941892 total,  3814124 used,   127768 free,    10344 buffers
KiB Swap:  7999484 total,  1254892 used,  6744592 free.   578856 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                           
 3139 bhavik    20   0 1566528 481200  29868 S  16.6 12.2  27:00.07 firefox                                                                           
 1562 root      20   0  421464  93532  75264 S   5.0  2.4   8:05.34 Xorg                                                                              
 3638 bhavik    20   0 1138384  68916   9424 S   4.6  1.7  16:20.09 zoiper                                                                            
 3272 bhavik    20   0  666728  16036   7024 S   3.7  0.4   0:22.53 gnome-terminal                                                                    
 2756 bhavik    20   0  520456  14812   8732 S   3.3  0.4   3:40.13 compiz                                                                            
 3011 bhavik    20   0  557576  77260  12584 S   2.3  2.0  13:01.57 skype                                                                             
 2933 bhavik    20   0  513136  15148   6400 S   2.0  0.4   2:02.75 indicator-apple                                                                   
 2771 bhavik    20   0 3016944 1.783g   5052 S   1.0 47.4   5:19.61 glipper                                                                           
 2702 bhavik     9 -11  513348   4172   2660 S   0.3  0.1   2:54.37 pulseaudio                                                                        
 3874 bhavik    20   0  802960  65136   9956 S   0.3  1.7   6:51.94 gedit                                                                             
 4125 bhavik    20   0 1051432  16708   1968 S   0.3  0.4   0:39.27 chromium-browse                                                                   
 7327 root      20   0   29144   1764   1172 R   0.3  0.0   0:00.04 top                                                                               
    1 root      20   0   33896   2132    944 S   0.0  0.1   0:01.55 init                                                                              
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                                          
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.14 ksoftirqd/0                                                                       
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                      
    7 root      20   0       0      0      0 R   0.0  0.0   0:07.93 rcu_sched                                                                         
    8 root      20   0       0      0      0 S   0.0  0.0   0:03.47 rcuos/0                                                                           
    9 root      20   0       0      0      0 S   0.0  0.0   0:02.14 rcuos/1                                                                           
   10 root      20   0       0      0      0 S   0.0  0.0   0:03.64 rcuos/2                                                                           
   11 root      20   0       0      0      0 S   0.0  0.0   0:02.45 rcuos/3                                                                           
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/4                                                                           
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/5                                                                           
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/6                                                                           
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/7                                                                           
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                                                            
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0                                                                           
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1                                                                           

```

---

### Post by QIII on 2015-03-30
Hello!

Glipper (the GNOME clipboard) is accounting for nearly half of your memory.

Either use its menu to clear the contents or kill the process by executing the command

```
 killall glipper 
```

In the terminal.

Let us know the results.

Cheers!

---

### Post by v3.xx on 2015-03-30
glipper
> VIRT------RES------SHR----%MEM
3016944---1.783g---5052---47.4
[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management#The_difference_among_VIRT.2C_RES.2C_and_SHR_in_top_output](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management#The_difference_among_VIRT.2C_RES.2C_and_SHR_in_top_output)

I just installed glipper and it runs out of the box using 13M of ram.  Why is yours so loaded?  If you can kill this program, your system should see a big improvment.  I say if you can kill it because I am not a user of this clip manager and do not know the constituencies (if any) of shutting it down.
```
killall glipper
```

EDIT:
Ok, should of reloaded the page before posting :rolleyes:

---


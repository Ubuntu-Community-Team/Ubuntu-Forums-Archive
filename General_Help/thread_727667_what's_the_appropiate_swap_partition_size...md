---
title: "what's the appropiate swap partition size.."
date: 2008-03-18
forum: General Help
---

### Post by Mia_tech on 2008-03-18
I have a 1G RAM, and I have partitioned my swap with a 2G, but now it's allocating lots of swap memory without even using half of RAM... I wonder what's the appropiate ratio to calculate the swap space?.. and also if I want to resize my swap space do I have to repartition the entire disk and reinstall the OS?

thanks

---

### Post by kpkeerthi on 2008-03-18
The recommeded swap partition size is about 1.5 to 2 times the amount of RAM. Your swap size is just about right size.
Can you post a screenshot of **top** command running in a termial? Also the output of **free -m** ?

You don't have to reinstall OS to resize partition. You can use [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to alter your partitions. Although it has never failed on me, it is advisable to backup before modifying partitions.

---

### Post by kuja on 2008-03-18
With a GiB of RAM, you might be able to get away with no swap at all, depending on your typical usage. I've got two GiB and the swap almost never gets touched ... I'd say it were a waste of hard drive space if I didn't need at least 1x my amount of RAM to put it into hibernate.

---

### Post by Mia_tech on 2008-03-18
> **kpkeerthi said:**
> The recommeded swap partition size is about 1.5 to 2 times the amount of RAM. Your swap size is just about right size.
Can you post a screenshot of **top** command running in a termial? Also the output of **free -m** ?

You don't have to reinstall OS to resize partition. You can use [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to alter your partitions. Although it has never failed on me, it is advisable to backup before modifying partitions.

yes, I booted with a live cd and resize the swap space, to a 1G, to force the system to use less space of swap and more memory, I don't know if the system is using swap b/c I'm using 64 bit version...also the system tends to get slow when I started working with vmware server and open 2 or 3 vm's at a time, plus the regular firefox, thunderbird etc...I will post what u ask as soon as I get all my apps running..

thanks

---

### Post by housam on 2008-03-18
I have 1 GB of RAM and 1 GB of swap . it never exceed 300 MB of swap for any operation done while the RAM is used by 250 MB.

---

### Post by anantshri on 2008-03-18
well my method of working say if you have more then 1.5GB of ram you can go without swap and you will recieve a performance upgrade,

actually with swap present linux kernel always tries to maximise its usage and avoid more ram consumption, but with ram of size 1.5GB or more i don't find swap as a absolute requirement.

---

### Post by kpkeerthi on 2008-03-18
> **Mia_tech said:**
> I will post what u ask as soon as I get all my apps running..
thanks

You can see with the **top** and **free -m** commands how much swap ubuntu 'actually sees'. You don't have to have all apps running. I just want to make sure if ubuntu is really **seeing** 2 GB you have alloted.

---

### Post by erginemr on 2008-03-18
For further reading on swap:
[http://ubuntuforums.org/showthread.php?t=252206&highlight=swap](http://ubuntuforums.org/showthread.php?t=252206&highlight=swap)

---

### Post by erginemr on 2008-03-18
You may also turn your attention to a system setting called **swappiness**, which instructs the kernel on how much swap it will use:
[http://ubuntuforums.org/showthread.php?t=712625&highlight=swappiness](http://ubuntuforums.org/showthread.php?t=712625&highlight=swappiness)
[http://ubuntuforums.org/showthread.php?t=406115&highlight=swappiness](http://ubuntuforums.org/showthread.php?t=406115&highlight=swappiness)
[http://ubuntuforums.org/showthread.php?t=650092&highlight=swappiness](http://ubuntuforums.org/showthread.php?t=650092&highlight=swappiness)

---

### Post by Mia_tech on 2008-03-18
> **kpkeerthi said:**
> You can see with the **top** and **free -m** commands how much swap ubuntu 'actually sees'. You don't have to have all apps running. I just want to make sure if ubuntu is really **seeing** 2 GB you have alloted.

ok, I think there are discrepancies between the system monitor and top... here's the top output
```
top - 02:58:13 up 26 min,  2 users,  load average: 0.82, 3.01, 3.39
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.8%us,  0.5%sy,  0.0%ni, 94.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    963696k total,   953552k used,    10144k free,     9276k buffers
Swap:        0k total,        0k used,        0k free,   604008k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6249 root      15   0  275m  27m 7820 S    7  2.9   0:59.06 Xorg               
 6462 jorge     16   0  208m  20m  14m S    3  2.2   0:07.14 gnome-system-mo    
 6324 jorge     15   0  112m 9.9m 7544 S    0  1.1   0:00.69 metacity           
 6460 jorge     15   0 19084 1340  972 R    0  0.1   0:00.98 top                
    1 root      18   0  5112 1468   68 S    0  0.2   0:01.71 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      17  -5     0    0    0 S    0  0.0   0:00.01 khelper            
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   31 root      10  -5     0    0    0 S    0  0.0   0:00.12 kblockd/1    
```

here's free -m
```
jorge@ubuntu-box:~$ sudo free -m
[sudo] password for jorge:
             total       used       free     shared    buffers     cached
Mem:           941        932          8          0          9        583
-/+ buffers/cache:        339        601
Swap:            0          0          0

```

attached is what sys mon thinks it's been used...

thanks

---

### Post by kpkeerthi on 2008-03-18
Unfortunately, your Ubuntu failed to detect your swap partition. (usually happens after you alter your swap partition with gparted)
> 
Swap:      **  0k total,        0k used**,        0k free,   604008k cached


You need to set your swap partition using this command
```
sudo swapon /dev/sda2*
```

* Change /dev/sda2 to whatever your swap partition is.

Also make sure your swap is set in /etc/fstab so it 'sticks' across reboots.

---

### Post by kpkeerthi on 2008-03-18
After you set swap with **swapon** run the **top** command again and make sure it reports its size.

---

### Post by erginemr on 2008-03-18
I always wonder why, but top seems to report the memory/swap usage erroneously. It is as if the system locks down the complete memory and uses it whenever needed, yet the traditional CLI commands "top" and "free" cannot see this and thus, cannot report the amount of free memory correctly. In this context, I find the report by the "gnome-system-monitor" much more reliable.

So, I suggest you to install and use "htop" instead. You can use it from the command line, but the installer will also place a shortcut to the "System Tools" submenu of the Gnome applications menu. You can install "htop" with:
```
sudo aptitude install htop
```

IMHO, "htop" has a few advantages over the classical tool "top". For one, it is more responsive against keyboard input; it is colorized; and last but not least, it reports the memory usage correctly. 

To be able to use the function keys (F1-10) at the bottom of htop while viewing it from under gnome-terminal, you can use the menu of gnome-terminal, and then "keyboard shortcuts..." to disable menu shortcut keys such as F1 and F10.

---

### Post by HunterK on 2008-03-18
> **Mia_tech said:**
> ok, I think there are discrepancies between the system monitor and top... here's the top output
```
top - 02:58:13 up 26 min,  2 users,  load average: 0.82, 3.01, 3.39
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.8%us,  0.5%sy,  0.0%ni, 94.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    963696k total,   953552k used,    10144k free,     9276k buffers
Swap:        0k total,        0k used,        0k free,   604008k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6249 root      15   0  275m  27m 7820 S    7  2.9   0:59.06 Xorg               
 6462 jorge     16   0  208m  20m  14m S    3  2.2   0:07.14 gnome-system-mo    
 6324 jorge     15   0  112m 9.9m 7544 S    0  1.1   0:00.69 metacity           
 6460 jorge     15   0 19084 1340  972 R    0  0.1   0:00.98 top                
    1 root      18   0  5112 1468   68 S    0  0.2   0:01.71 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      17  -5     0    0    0 S    0  0.0   0:00.01 khelper            
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   31 root      10  -5     0    0    0 S    0  0.0   0:00.12 kblockd/1    
```

here's free -m
```
jorge@ubuntu-box:~$ sudo free -m
[sudo] password for jorge:
             total       used       free     shared    buffers     cached
Mem:           941        932          8          0          9        583
-/+ buffers/cache:        339        601
Swap:            0          0          0

```

attached is what sys mon thinks it's been used...

thanks

Whoa, your swap isn't even being detected by Ubuntu.  0KB of ***0KB*** used!  It would say the total swap size in the sys mon screenshot.

You need to find out what label your swap has and make sure it is being mounted correctly via fstab.  This happened to me yesterday when I resized my swap / deleted other partitions.  My swap became /dev/sda2 instead of /dev/sda3 like before.

---

### Post by Mia_tech on 2008-03-18
ok, I've decided to backup and reinstall the i386 version which in my experience has work better, I just wanted to try the 64 bit experience...let you all know the latest news ;O)

Thanks

---

### Post by Mia_tech on 2008-03-18
ok...when I open vmware is still crashing down my desktop, here's the top output
```
top - 16:48:56 up  1:00,  4 users,  load average: 0.57, 0.53, 1.36
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  1.0%sy,  0.0%ni, 94.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    969472k total,   954920k used,    14552k free,     3840k buffers
Swap:  1951888k total,   117004k used,  1834884k free,   663316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
15085 root      15   0  247m  20m  11m S    7  2.1   2:35.57 Xorg               
15462 jorge     15   0 48960  11m 8964 S    2  1.2   0:36.76 gnome-system-mo    
15518 jorge      5 -10  425m 206m 187m S    1 21.8   0:34.28 vmware-vmx         
15545 jorge      5 -10  363m 261m 252m S    1 27.7   0:40.57 vmware-vmx         
 4625 root      10  -5     0    0    0 S    1  0.0   0:03.23 kondemand/0        
15326 jorge     15   0 91728  17m 8236 R    0  1.9   0:01.47 gnome-terminal     
15671 jorge     15   0  2364 1172  876 R    0  0.1   0:00.04 top                
    1 root      15   0  2948  260  204 S    0  0.0   0:01.27 init               
    2 root      17  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/1           

```

here's the free -m output:
```
jorge@ubuntu-box:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           946        930         16          0          4        651
-/+ buffers/cache:        274        672
Swap:         1906        114       1791

```

---

### Post by kpkeerthi on 2008-03-19
> **Mia_tech said:**
> ok, I've decided to backup and reinstall the i386 version which in my experience has work better, I just wanted to try the 64 bit experience...let you all know the latest news ;O)

Thanks

Are you sure you want to do this? How much virtual RAM do you have allocated for your guest OS? 

The host machine has 1 GB RAM. So I suggest you give not more than 256MB for your Guest OS or else you will find your **host **begin to swap sooner. 

Reduce your virtual RAM and see how stable your Guest OS is before you want to re-install.

---

### Post by Mia_tech on 2008-03-19
oh, I've already reinstalled no big deal, and in my opinion is already working better...I always set my gues machines in vm with 256 or ram, but vmware is very memory consuming specially when you have 2 or 3 machines running at a time...

thanks

---

### Post by Mia_tech on 2008-03-19
> **kpkeerthi said:**
> Are you sure you want to do this? How much virtual RAM do you have allocated for your guest OS? 

The host machine has 1 GB RAM. So I suggest you give not more than 256MB for your Guest OS or else you will find your **host **begin to swap sooner. 

Reduce your virtual RAM and see how stable your Guest OS is before you want to re-install.

can you explain what the "buffers" and "cached" section in the TOP command means?

thanks

---

### Post by kpkeerthi on 2008-03-19
> **Mia_tech said:**
> oh, I've already reinstalled no big deal, and in my opinion is already working better...I always set my gues machines in vm with 256 or ram, but vmware is very memory consuming specially when you have 2 or 3 machines running at a time...

thanks

Reinstallation is not a solution for problems like this. Perhaps this is is not a problem - the heavy swapping you experienced is purely attributed to your 2 or 3 virtual machines running simutaneously. That is to be expected - you are running processes on top of ubuntu that are OSes per se. 

Anyway I think you made up your mind to reinstall and I seriously doubt the reinstall eliminated the issue ( you are bound to placebo effect)

[What are buffers and cache?]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management#The_difference_between_buffers_and_cache")

---

### Post by Mia_tech on 2008-03-19
> **kpkeerthi said:**
> Reinstallation is not a solution for problems like this. Perhaps this is is not a problem - the heavy swapping you experienced is purely attributed to your 2 or 3 virtual machines running simutaneously. That is to be expected - you are running processes on top of ubuntu that are OSes per se. 

Anyway I think you made up your mind to reinstall and I seriously doubt the reinstall eliminated the issue ( you are bound to placebo effect)

[What are buffers and cache?]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management#The_difference_between_buffers_and_cache")

reinstallation for me worked..as I was running the 64bit version and now I'm running 32, and in my opinion is handling memory better

thanks

---


---
title: "MOTD memeory usage disagrees with free"
date: 2014-05-11
forum: General Help
---

### Post by pitviper101 on 2014-05-11
Why does my MOTD memory usage disagree with the output of free and top?
The MOTD message says I'm using 25% of my memory. 
The numbers free put out say I'm using about 60%. 
Top shows the same numbers for total, used and free. However the sum of the percentages used by all processes is about 11 even when assuming and accounting for all of top's percentages being rounded down to the nearest tenth of a percent.
MOTD and free:
```
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-61-generic x86_64)

 * Documentation:  https://help.ubuntu.com/


  System information as of Sun May 11 12:35:25 MDT 2014


  System load:  0.0                Processes:           118
  Usage of /:   6.1% of 179.74GB   Users logged in:     1
  Memory usage: 25%                IP address for eth0: 192.168.1.2
  Swap usage:   0%                 IP address for eth1: 192.168.2.2


  Graph this data and manage this system at https://landscape.canonical.com/


No mail.
Last login: Sun May 11 12:14:12 2014 from shorty
james@hacksawu2:~$ free
             total       used       free     shared    buffers     cached
Mem:       3744532    2268064    1476468          0     480816    1402504
-/+ buffers/cache:     384744    3359788
Swap:            0          0          0

```

Totals for running processes based on top sorted by memory usage (verified number with sudo ps aux | wc)
```
 1 x 1.2 = 1.2
 1 x 0.3 = 0.3
10 * 0.2 = 2.0%
12 * 0.1 = 1.2
120 *0.05= 6.0 //assume each processes was rounded down so add 0.049999 for each
Total    =10.7
Under 11%

```

Which number is right? Why do they disagree?

---

### Post by mcduck on 2014-05-11
Actually *free* is saying you are using about 10% of your RAM. ;)

You need to read from the "-/+ buffers/cache" -line to check how much of your RAM is used by running processes. 

The first line includes any buffers and cached data, and will eventually grow to close to 100% after the system has been running for a while as recently used data gets stored in cache in case it's needed again. From any program's perspective the cache still counts as free and available memory since it can be immediately dropped if some process needs more memory.

(What comes to MOTD giving you higher vale, I'd assume it actually *was* higher when the message was created, as there were more things happening at the time. That's of course hard to check without having top running while you log in so you'd be able to compare the values from the same moment in time...)

---


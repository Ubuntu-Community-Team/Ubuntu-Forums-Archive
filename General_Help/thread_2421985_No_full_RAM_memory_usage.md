---
title: "No full RAM memory usage"
date: 2019-06-30
forum: General Help
---

### Post by pkozienk on 2019-06-30
Hello,
I have a virtual machine on Google with **4TB RAM** to execute a script creating tables (based on HASHTABLE ENTRY).
I am asking with a polite inquiry - how to fully use the capabilities of this machine to speed up the process of creating tables? 
I have the impression that Ubuntu configuration issues cause incomplete use of resources, so I prefer to be sure than to waste unnecessary time due to ignorance. 

Here are the commands for the process with "htop" (process name - test.exe):

[IMG]https://i.ibb.co/88sX7xv/htop.png[/IMG]
...as much as the value of VIRT probably results from the configuration of the script itself (such is the demand for the current configuration of the operating mode setting), so my attention is drawn by the value of RES and MEM. Any tips?


Here are some snapshots of the system after my changes in limits.conf:
**********
***ulimit -a:***     *
**********
[IMG]https://i.ibb.co/Jk2Z2BV/ulimit.png[/IMG]
********
[U][B]free -m:*
[/B][/U]********
[IMG]https://i.ibb.co/c1v8x48/free.png[/IMG]
[IMG]https://ibb.co/xDsg3xg[/IMG]

========================
My system is Ubuntu 16.04 LTS  64bit

---

### Post by Doug S on 2019-06-30
Interesting.
I do not understand your output for "free -m", as it suggests you only have ~4 gigabytes of ram. did you mean to write "free -g"?

I have an old program used to test how much memory I can allocate. It would need to be modified for your purpose, but might be worth trying. I limit it, because it starts to use swap (it did not used to use swap). You don't have any swap, so that part should be O.K. without needing to use mlock and such. Perhaps limit your test to 3.8 Terabytes so that your machine doesn't crash with OOM (Out Of Memory).

```
/*****************************************************************************
*
* testm.cpp 2013.01.06 Smythies
*           added a couple more sleeps, in attempts to observe stuff on linux.
*
* testm.cpp 2010.12.14 Smythies
*           attempt to compile on Ubuntu Linux.
*
* testm.cpp 2009:03:18 Smythies
*           This is not the first edit, but I am just adding the history
*           header.
*           How much memory can this one program ask for and sucessfully get?
*           Done in two calls, to more accurately simulate the program I
*           and wondering about.
*           This edit is a simple change to print the total.
*           the sleep calls have changed (again) for MS C version 2008.
*           Now they are more like they used to be (getting annoying).
*                                                                     Smythies
*****************************************************************************/

#include <stdio.h>
#include <stdlib.h>

#define CR 13

int main(){
   char *fptr;
   char *fptr1;
   long i, j, k;

//   i = 8589934596L;
//   j = 8589934596L;
//   i = 9000000000L;
//   j = 9000000000L;
   i = 12000000000L;
   j = 12000000000L;



   do{
      if(( fptr = (char *)malloc(i)) == NULL){
         i = i - 1000;
      }
   }
   while (( fptr == NULL) && (i > 0));
   sleep(15);  /* for time to observe */
   for(k = 0; k < i; k++){   /* so that the memory really gets allocated and not just reserved */
      fptr[k] = (char) (k & 255);
   } /* endfor */
   sleep(15);  /* so that I can observe on perfmon */
   do{
      if(( fptr1 = (char *)malloc(j)) == NULL){
         j = j - 1000;
      }
   }
   while (( fptr1 == NULL) && (j > 0));
   sleep(15);  /* for time to observe */
   for(k = 0; k < j; k++){   /* so that the memory really gets allocated and not just reserved */
      fptr1[k] = (char) (k & 255);
   } /* endfor */
   printf("Allocated: %ld   Allocated1: %ld   Total: %ld\n",i,j, i + j);
   printf("Total KiloBytes: %12.2lf   Total MegaBytes: %9.2lf   Total Gigabytes: %6.3lf\n",(double) (i + j) / 1024.0, (double) (i + j) / 1024.0 / 1024.0,  (double) (i + j) / 1024.0 / 1024.0 / 1024.0);

   sleep(15);  /* so that I can observe */
   free(fptr);
   sleep(15);  /* so that I can observe */
   free(fptr1);
   sleep(15);  /* so that I can observe */
   return(0);
}

```I usually run "watch free -m" in another terminal while it runs. Example:

```
doug@s15:~/c$ ./testm
Allocated: 12000000000   Allocated1: 12000000000   Total: 24000000000
Total KiloBytes:  23437500.00   Total MegaBytes:  22888.18   Total Gigabytes: 22.352
```and```
Every 2.0s: free -m                                                                                                                                                            Sun Jun 30 07:34:15 2019

              total        used        free      shared  buff/cache   available
Mem:          15743       15441         129           0         172          77
Swap:         16085        4652       11433

```and```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
28456 doug      20   0 22.356g 0.014t    960 R   9.5 96.1   0:59.07 testm
  172 root      20   0       0      0      0 D   5.2  0.0   1:46.01 kswapd0
  498 root       0 -20       0      0      0 I   1.8  0.0   1:08.62 kworker/2:1H-kb
28628 root      20   0   52292   2788   2408 D   1.4  0.0   0:00.08 cron

```

---

### Post by pkozienk on 2019-06-30
It is free -g dump:
             
```

         ** total        used        free      shared  buff/cache   available**
Mem:  3783         1027        2755           0                1               2745
Swap:   0                0              0

```

Your script is executed normally, its result:
```

Allocated:  12000000000   Allocated1: 12000000000   Total: 24000000000
Total KiloBytes:  23437500.00   Total MegaBytes:  22888.18   Total Gigabytes: 22.352

```

I note that I started it up DURING the process by which it spreads, because I've been pulling it for several hours and I do not intend to kill it without a specific argument, which will be information about the existence of the drug for acceleration :-)

To be sure - I will remind you again: the number of RAM you have at my disposal (now with an accuracy of one) = _**3 844 GB**_

---

### Post by TheFu on 2019-06-30
I have zero clue about using Google's infra.  Think they run an optimized, stripped-down, KVM hypervisor.

You've asked a question that requires detailed knowledge about what your program(s) do.  Is the hash table in RAM, using a commonly used file-based DB, using a custom file-based DB, using NoSQL or using some RDMBS?  The solution to improve performance for each would be vastly different.

A little background about the tools used would help greatly.

We have to figure out what is causing the slowdown.  My eyes cannot read the color output in those images. Sorry.  Blue, red and green are particularly bad for me. I use bright green/yellow on a black background myself with color output disabled for everything.

If you could post using code-tags and text, that would help greatly (while saving bandwidth for people who pay by the bit). Then I can scale the text here to read it.  Or not - your choice.

Do you have system monitoring installed on the VM?  Munin, monit, sysusage, nagios, cacti, anything?  Then we could see where any throttling is happening.
CPU
RAM
Disk I/O
Network I/O
something else?

Often, if you are CPU bound, then either splitting up the task into separate processes or threads is the easiest answer. Just depends on the data involved. That's why facebook can scale out so easily compared to shared transactional DBs which have to go through effectively a single writing process. Splitting into separate processes can have the added benefit of helping with any per-CPU memory access limitations or performance issues.  Ubuntu's kernel doesn't limit per process RAM from what I can see. I checked some of my 16.04  systems today. None have limits.

On  servers, different RAM chips are closer to different CPUs, so accessing RAM on a foreign CPU is slower.  To know the details around that, you'd need to have access about the physical hardware and how the VM was setup for RAM-to-CPU affinity.  I've never had to deal with this myself, but know it exists.  In a prior job, looking at detailed server architectures and picking the best for our needs was something I did, though I didn't do that for PC-servers, just PA-RISC, PowerX, UltraSPARC, and a few other commercial Unix providers.

Tuning is about handling each issue as they are discovered, then handling the next and the next until either time or money run out. ;)
OTOH, we often spend a week trying to optimize a task that if we'd just let run the first day, it would have completed in under 2 days.  Always consider the trade-off for "fastest solution time."  But if you will need to do this task monthly for the next 3 yrs, then tuning it would be very worth while.

---

### Post by Doug S on 2019-06-30
> **pkozienk said:**
> 
Your script is executed normally, its result:
```

Allocated:  12000000000   Allocated1: 12000000000   Total: 24000000000
Total KiloBytes:  23437500.00   Total MegaBytes:  22888.18   Total Gigabytes: 22.352

```Yes, you need to increase the limits, a lot.

---

### Post by pkozienk on 2019-06-30
> **TheFu said:**
> I have zero clue about using Google's infra.  Think they run an optimized, stripped-down, KVM hypervisor.

You've asked a question that requires detailed knowledge about what your program(s) do.  Is the hash table in RAM, using a commonly used file-based DB, using a custom file-based DB, using NoSQL or using some RDMBS?  The solution to improve performance for each would be vastly different.

A little background about the tools used would help greatly.

We have to figure out what is causing the slowdown.  My eyes cannot read the color output in those images. Sorry.  Blue, red and green are particularly bad for me. I use bright green/yellow on a black background myself with color output disabled for everything.

If you could post using code-tags and text, that would help greatly (while saving bandwidth for people who pay by the bit). Then I can scale the text here to read it.  Or not - your choice.

Do you have system monitoring installed on the VM?  Munin, monit, sysusage, nagios, cacti, anything?  Then we could see where any throttling is happening.
CPU
RAM
Disk I/O
Network I/O
something else?

Often, if you are CPU bound, then either splitting up the task into separate processes or threads is the easiest answer. Just depends on the data involved. That's why facebook can scale out so easily compared to shared transactional DBs which have to go through effectively a single writing process. Splitting into separate processes can have the added benefit of helping with any per-CPU memory access limitations or performance issues.  Ubuntu's kernel doesn't limit per process RAM from what I can see. I checked some of my 16.04  systems today. None have limits.

On  servers, different RAM chips are closer to different CPUs, so accessing RAM on a foreign CPU is slower.  To know the details around that, you'd need to have access about the physical hardware and how the VM was setup for RAM-to-CPU affinity.  I've never had to deal with this myself, but know it exists.  In a prior job, looking at detailed server architectures and picking the best for our needs was something I did, though I didn't do that for PC-servers, just PA-RISC, PowerX, UltraSPARC, and a few other commercial Unix providers.

Tuning is about handling each issue as they are discovered, then handling the next and the next until either time or money run out. ;)
OTOH, we often spend a week trying to optimize a task that if we'd just let run the first day, it would have completed in under 2 days.  Always consider the trade-off for "fastest solution time."  But if you will need to do this task monthly for the next 3 yrs, then tuning it would be very worth while.

What's better, worse, probably would be possible if it was not for the fact that it is Google's cloud and I do not have (and I will not) the possibility of interfering / physically touching the hardware ... It is also certain that Google does not limit Ubuntu's capabilities with its overlays, because they offer machines of various sizes just so that you can use them.
I will execute the script once (I will not repeat the steps).
The whole process happens "in memory" and no external modules are used outside the secp256k1 library.
Specifically - a script based on [https://en.wikipedia.org/wiki/Baby-step_giant-step](https://en.wikipedia.org/wiki/Baby-step_giant-step) is executed


I do not have any ingredients from those mentioned by you, because I have never needed it and I do not know about it. If it will be helpful - I am asking for directions - I will throw in the screenshot as soon as I find out what is needed.

---


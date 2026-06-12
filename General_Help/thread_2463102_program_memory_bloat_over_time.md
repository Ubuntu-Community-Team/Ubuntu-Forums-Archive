---
title: "program memory bloat over time"
date: 2021-06-03
forum: General Help
---

### Post by Unguidedone on 2021-06-03
When i start up my machine it normally gets all applications running to about 17 gigs in ram then 24 hours later its at 24 gigs in ram.  If i leave it up for a week i can reach about 30 gigs.  I open and close my file manager and it decreases memory footprint same with every program opened.  Can we set max allowed memory per application then autorestart when limit is reached?  firefox uses 10-20 gigs of memory and i have about 50-100 tabs up + a few hundred(s) more i have closed in a single session.

how do we get this memory footprint down?

---

### Post by QIII on 2021-06-03
What on earth are you running that consumes that much memory starting out?  That's a problem right there.

---

### Post by ActionParsnip on 2021-06-04
Have you used the "top" command to see if it is the browser using all the RAM?

---

### Post by grahammechanical on 2021-06-04
The operating system allocates memory (RAM) to applications as each application demands memory and at the same time the OS sets aside a similar amount of memory in a cache or buffer in readiness for the application to need more memory. The RAM is there to be used and so the OS makes use of it.

When an application is closed allocation of memory is freed. When all the memory is used then the OS starts swapping application code in and out of memory. The time to worry about excessive memory use is when the desktop freezes.

It helps if we are given information about the hardware and the use it is being put to. 

Regards.

---

### Post by scorp123 on 2021-06-04
> **Unguidedone said:**
>  When i start up my machine it normally gets all applications running to about 17 gigs in ram then 24 hours later its at 24 gigs in ram. 

Doesn't need to be a problem + your description is too vague. Please provide more information? e.g. the output of these commands:
```
free -h
top -b -n1
```


> **Unguidedone said:**
>  If i leave it up for a week i can reach about 30 gigs. ...

As I said above: doesn't mean there's a problem. If you have 32 GiB of RAM then using 30 is fine. Different story if you only have 8 GiB...  Please provide the command outputs I asked above. Then we will see...

---

### Post by ajgreeny on 2021-06-04
I can not believe that you really need 50-100 tabs open on Firefox; there is no way you can need all of them open at the same time, surely?  Even if you insist that they are necessary, firefox using 10-20G of ram seems inconsistent with my memory use by firefox, though I seldom have more than 5 or 6 tabs open at any time.

And an autorestart of any program would be worse than simply closing the application as you will lose any unsaved work.

I suspect that you either are getting incorrect figures for use of your RAM, or that you have something very wrong with your whole OS as suggested by QIII above.

---

### Post by TheFu on 2021-06-04
Firefox lies about RAM use.  It might have huge virtual allocations, but only use 500MB in reality.
For example
```
13794 thefu        20   0 [COLOR="#FF0000"]27.136g[/COLOR] [COLOR="#00FF00"]269984[/COLOR]  61252 S   0.3  0.8 183:10.10 WebExtensions
```

That's firefox claiming to be using 27G, but actually using 270MB.  The system has been up 20 days.
What that also means is that firefox extensions have huge memory leaks.  If I run for a few days without any extensions (painful), then that number doesn't get large.

There are ways to limit per-process RAM use.  There is the system-wide limit ... which is for every process on the system. There are per-userid limits, which are for each userid.  **ulimit** and **bash**
There are per process limits too. **prlimit**  Works based on the PID.

These days, people might use either a Linux container or cgroups/namespaces.  **firejail** can limit the RSS memory using the --rlimit-as= option, for example.

To get the current information about a process, we have to use the PID.
```
$ prlimit --pid 13456
RESOURCE   DESCRIPTION                             SOFT      HARD UNITS
AS         address space limit                unlimited unlimited bytes
CORE       max core file size                         0 unlimited bytes
CPU        CPU time                           unlimited unlimited seconds
DATA       max data size                      unlimited unlimited bytes
FSIZE      max file size                      unlimited unlimited bytes
LOCKS      max number of file locks held      unlimited unlimited locks
MEMLOCK    max locked-in-memory address space  67108864  67108864 bytes
MSGQUEUE   max bytes in POSIX mqueues            819200    819200 bytes
NICE       max nice prio allowed to raise             0         0 
NOFILE     max number of open files                4096   1048576 files
NPROC      max number of processes               127893    127893 processes
RSS        max resident set size              unlimited unlimited bytes
RTPRIO     max real-time priority                     0         0 
RTTIME     timeout for real-time tasks            50000    200000 microsecs
SIGPENDING max number of pending signals         127893    127893 signals
STACK      max stack size                       8388608 unlimited bytes
```
That's for my firefox instance running under a firejail.
```
$ prlimit --pid 13456 --rss
RESOURCE DESCRIPTION                SOFT      HARD UNITS
RSS      max resident set size unlimited unlimited bytes
```

For fun, ran a fresh firefox in a private firejail with a 4G address space limit.
```
$ prlimit --pid 31525
RESOURCE   DESCRIPTION                              SOFT       HARD UNITS
AS         address space limit                [COLOR="#00FF00"]4096000000 4096000000 bytes[/COLOR]
CORE       max core file size                          0  unlimited bytes
CPU        CPU time                            unlimited  unlimited seconds
DATA       max data size                       unlimited  unlimited bytes
FSIZE      max file size                       unlimited  unlimited bytes
LOCKS      max number of file locks held       unlimited  unlimited locks
MEMLOCK    max locked-in-memory address space   67108864   67108864 bytes
MSGQUEUE   max bytes in POSIX mqueues             819200     819200 bytes
NICE       max nice prio allowed to raise              0          0 
NOFILE     max number of open files                 4096    1048576 files
NPROC      max number of processes                127893     127893 processes
RSS        max resident set size               unlimited  unlimited bytes
RTPRIO     max real-time priority                      0          0 
RTTIME     timeout for real-time tasks             50000     200000 microsecs
SIGPENDING max number of pending signals          127893     127893 signals
STACK      max stack size                        8388608  unlimited bytes
```

At my next reboot, the 4G address space limit will be set for firefox and I'll see what happens.  I did go and visit a very complex webapp with the private firejail and firefox.
```
$ top -b |grep -i webexte
13794 thefu        20   0 27.134g 258584  61608 S   0.0  0.8 183:20.45 WebExtensions
31612 thefu        20   0 2591360 104684  83748 S   0.0  0.3   0:00.65 WebExtensions

```
The old (27G) and the new (2.5MB).  In a private firejail, no prior settings are visible, no extensions, not profile, no history.  It is like running firefox in "safe" mode, but nothing can be written to any storage either, at least not permanently.

---


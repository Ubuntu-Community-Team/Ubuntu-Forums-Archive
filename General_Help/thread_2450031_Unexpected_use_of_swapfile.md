---
title: "Unexpected use of swapfile"
date: 2020-09-06
forum: General Help
---

### Post by David_Partridge on 2020-09-06
I've added some free storage monitoring using cron to my system after the problem I recently had with no swapfile.

free -h says:

```

              total        used        free      shared  buff/cache   available
Mem:           7.5G        1.2G        144M         46M        6.1G        5.9G
Swap:           15G         85M         15G

```

I don't understand why there's 85M of swapfile in use when there's loads of unused RAM.

Please could a kind soul explain.

Thanks
David

---

### Post by vanadium on 2020-09-06
At one time, there was a need to swap something away. It is only retrieved back to RAM when it is actually needed. Apparently, there was no need, so it stayed in SWAP instead of occupying RAM that has better use for something else.

---

### Post by SeijiSensei on 2020-09-06
I believe some components of the kernel are always stored in swap, if it exists, even if there is physical memory available. If you run the command "ps ax" the items inside square brackets and preceded with a capital "S" are in swap.  E.g.,

```

PID TTY         STAT   TIME COMMAND 
      1 ?        Ss     1:30 /sbin/init splash
      2 ?        S      0:00 [kthreadd]
      3 ?        I<     0:00 [rcu_gp]
      4 ?        I<     0:00 [rcu_par_gp]
      6 ?        I<     0:00 [kworker/0:0H-kblockd]
      9 ?        I<     0:00 [mm_percpu_wq]
     10 ?        S      0:24 [ksoftirqd/0]
     11 ?        I      4:24 [rcu_sched]
     12 ?        S      0:05 [migration/0]
     13 ?        S      0:00 [idle_inject/0]
     14 ?        S      0:00 [cpuhp/0]
     15 ?        S      0:00 [cpuhp/1]
     16 ?        S      0:00 [idle_inject/1]
     17 ?        S      0:05 [migration/1]
     18 ?        S      0:21 [ksoftirqd/1]
     20 ?        I<     0:00 [kworker/1:0H-kblockd]
     21 ?        S      0:00 [cpuhp/2]
     22 ?        S      0:00 [idle_inject/2]
     23 ?        S      0:06 [migration/2]
     24 ?        S      0:18 [ksoftirqd/2]
etc.

```

---

### Post by zebra2 on 2020-09-06
to check 
cat /proc/sys/vm/swappiness

A normal default swappiness should be 60. 100 would mean always swap. 0 would mean never swap unless absolutely necessary. If you have a lot of ram you could set it to 10 (I suppose).  All of my machines are maxed out on ram and I have them set to 3.  swapfile is rarely used. 
a search for "swappiness" will get you all of the info you need.

---

### Post by Impavidus on 2020-09-07
Some things always in swap? I don't know about that.```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          7,7Gi       1,2Gi       5,4Gi        79Mi       1,1Gi       6,1Gi
Swap:         8,5Gi          0B       8,5Gi
$ ps ax
    PID TTY      STAT   TIME COMMAND
      1 ?        Ss     0:01 /sbin/init splash
      2 ?        S      0:00 [kthreadd]
      3 ?        I<     0:00 [rcu_gp]
      4 ?        I<     0:00 [rcu_par_gp]
      6 ?        I<     0:00 [kworker/0:0H-kblockd]
      8 ?        I<     0:00 [mm_percpu_wq]
      9 ?        S      0:00 [ksoftirqd/0]
     10 ?        I      0:05 [rcu_sched]
     11 ?        S      0:00 [migration/0]
     12 ?        S      0:00 [idle_inject/0]
     13 ?        I      0:00 [kworker/0:1-events]
     14 ?        S      0:00 [cpuhp/0]
     15 ?        S      0:00 [cpuhp/1]
...
```Since I increased ram to 8GB, I've never seen swap used. Swap use may be more common with longer uptimes. I kept swappiness at 60. (Yes, I know my swap is very large. It's what the installer did automatically when I first installed Ubuntu on this laptop. I never cared enough to change it.)

I don't know the finer details of swap management in Linux, but it's quite clever. Think of it this way: When a page of memory is copied to swap, it isn't necessarily dropped from ram immediately, and when a page from swap is copied back to ram, it can remain in swap as long as it isn't modified. A page present in both can be accessed rapidly, but can also be dropped rapidly if ram is needed for something else.

---

### Post by Yellow Pasque on 2020-09-07
> **zebra2 said:**
> A normal default swappiness should be 60. 100 would mean always swap. 0 would mean never swap unless absolutely necessary.

That's a bit simplified. Gory technical details: [https://lwn.net/Articles/83588/](https://lwn.net/Articles/83588/)

---

### Post by Impavidus on 2020-09-07
> **David_Partridge said:**
> I've added some free storage monitoring using cron to my system after the problem I recently had with no swapfile.

free -h says:

```

              total        used        free      shared  buff/cache   available
Mem:           7.5G        1.2G        144M         46M        6.1G        5.9G
Swap:           15G         85M         15G

```

I don't understand why there's 85M of swapfile in use when there's loads of unused RAM.

Please could a kind soul explain.

Thanks
David
There's only 144MB unused ram. 6.1GB is used for buffers and cache. Caching a file that's frequently used may be more useful than keeping application data that are never used in ram.

> **Yellow Pasque said:**
> That's a bit simplified. Gory technical details: [https://lwn.net/Articles/83588/](https://lwn.net/Articles/83588/)

Interesting read. It's 16 years old though, but I guess the basics haven't changed too much.

---

### Post by zebra2 on 2020-09-07
```

~$ free
              total        used        free      shared  buff/cache   available
Mem:       12136748     1551728     8562120      277332     2022900    10018476
Swap:       1358916           0     1358916 
```
```
 System:  Host: zebra2-Lenovo-110-15ISK Kernel: 5.8.0-18-generic x86_64 bits: 64 
  compiler: N/A Desktop: N/A wm: gnome-shell dm: GDM3 
  Distro: Ubuntu 20.10 (Groovy Gorilla) 

$DESKTOP_SESSION
ubuntu-wayland
$XDG_SESSION_TYPE
wayland
GNOME Shell 3.36.4
Version: 3.36.4-1ubuntu2~build1
loginctl type
Type=wayland

```

```

cat /proc/sys/vm/swappiness
3

```

---

### Post by SeijiSensei on 2020-09-07
deleted

As always, I sure do wish we could delete posts.

---

### Post by SeijiSensei on 2020-09-07
> **Impavidus said:**
> Since I increased ram to 8GB, I've never seen swap used. Swap use may be more common with longer uptimes. 
```

              total        used        free      shared  buff/cache   available
Mem:       16333200     4465924     1227184      175920    10640092    11355388
Swap:       2097148       **10764**     2086384

```
This machine is on constantly so maybe that's why. It's been on for 19 days now.  My server, which has been up for 70 days but has just 4 GB of memory, has a lot more in swap.

---


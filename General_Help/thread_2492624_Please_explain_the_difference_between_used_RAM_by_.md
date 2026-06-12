---
title: "Please explain the difference between used RAM by 'free' and 'htop'"
date: 2023-11-17
forum: General Help
---

### Post by sudodus on 2023-11-17
Checking for used RAM can be confusing because different tools show **different results for used RAM**. Can you explain how to interpret the results marked red in the screenshot?

The windows in the screenshot show the output from **[FONT=Courier New]htop[/FONT]** and **[FONT=Courier New]free -m[/FONT]**

```

* htop:    **[COLOR="#CC0000"]553[/COLOR]** M
* free -m: **[COLOR="#CC0000"]897[/COLOR]** M

```

I rebooted the live **Lubuntu Noble system** and the command history was different, and I had the following result, now as text (to make it easier for you to use the data), now with a greater difference, **[FONT=Courier New]free[/FONT]** indicates approx. twice as much used RAM as **[FONT=Courier New]htop[/FONT]**.
```

* free -mw: 1106 M
------------------
lubuntu@lubuntu:~$ free -mw
               total        used        free      shared     buffers       cache   available
Mem:           11834        **[COLOR="#CC0000"]1106[/COLOR]**        6909         294          15        4369       10727
Swap:           5917           0        5917
--------------------------------------------------------------------------------------------

* htop: 533 M
-------------
    0[|                                 2.6%] Tasks: 80, 173 thr, 105 kthr; 1 running
    1[|                                 0.6%] Load average: 0.03 0.09 0.15 
    2[|                                 0.6%] Uptime: 00:27:28
    3[|                                 0.6%]
  Mem[||||||||||||||||||          **[COLOR="#CC0000"]533M[/COLOR]**/11.6G]
  Swp[                              0K/5.78G]

  [Main] [I/O]
    PID USER       PRI  NI  VIRT   RES   SHR S  CPU%&#9661;MEM%   TIME+  Command
   1396 root        20   0  788M  107M 65556 S   1.9  0.9  0:34.71 /usr/lib/xorg/Xorg -nolis
   2658 lubuntu     20   0  611M 50248 39716 S   1.3  0.4  0:04.48 /usr/libexec/gnome-termin
   2730 lubuntu     20   0 11348  4608  3584 R   2.6  0.0  0:08.45 htop
   1431 root        20   0  788M  107M 65556 S   1.3  0.9  0:05.02 /usr/lib/xorg/Xorg -nolis
   1792 lubuntu     20   0 1196M  109M 90304 S   0.0  0.9  0:04.04 /usr/bin/pcmanfm-qt --des
   1725 lubuntu     20   0  439M 28720 22296 S   0.0  0.2  0:02.18 /usr/bin/openbox
   1806 lubuntu     20   0 1196M  109M 90304 S   0.0  0.9  0:00.44 /usr/bin/pcmanfm-qt --des
      1 root        20   0  166M 14320  9200 S   0.0  0.1  0:03.45 /sbin/init splash ---
    848 root        19  -1 25528  9216  8320 S   0.0  0.1  0:00.29 /lib/systemd/systemd-jour
    879 root        20   0 29304  7576  4504 S   0.0  0.1  0:02.19 /lib/systemd/systemd-udev
   1124 systemd-re  20   0 20940 12544 10368 S   0.0  0.1  0:00.19 /lib/systemd/systemd-reso
F1Help  F2Setup F3SearchF4FilterF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit  

```

Can this be explained, or should we suspect that one of the tools is buggy in Noble? I do not see such differences in 22.04.3 LTS (Jammy).

[hr][/hr]
What about the content of **[FONT=Courier New]/proc/meminfo[/FONT]** ? Would it help to post matching data from there (with a new set of data from **[FONT=Courier New]free[/FONT]** and **[FONT=Courier New]htop[/FONT]**)?

---

### Post by VMC on 2023-11-17
I use 'vmstat -s', I know there are wide differences between commands.

---

### Post by MAFoElffen on 2023-11-17
If you look in /proc/meminfo, that has a better breakdone. put that in one window, the second window look at htop, then in the third window do free...

The difference seen between free and htop is because of the way they calculate the free memory. The basic summarized version is that  htop is counting cached memory as used but free is not. The following is my workstation

HTOP:
```

Mem[|||   2.5G/[COLOR=#008000]126G[/COLOR]]

```
free:
```

               total        used        free      shared  buff/cache   available
Mem:       131651668     3354964   127687072       21980      609632   [COLOR=#ff0000]127174440[/COLOR]

```
/proc/meminfo
```

grep . /proc/meminfo
MemTotal:       131651668 kB
MemFree:        [COLOR=#ff0000]127101848[/COLOR] kB
MemAvailable:   [COLOR=#008000]126732584[/COLOR] kB
Buffers:           72896 kB
Cached:           594148 kB
SwapCached:            0 kB
Active:           295084 kB
...

```
The color coding there shows were the numbers are coming from...

htop total available = page cache + reclaim - shared memory

free total available = page cache + slab reclaimable

Does that difference make sense now?

The number in Linux that really matters when things get tight is
```

mafoelffen@msi-ubuntu:~$ grep 'MemAvailable' /proc/meminfo
MemAvailable:   127858552 kB

```

---

### Post by sudodus on 2023-11-18
Thanks VMC and MAFoElffen,

When looping
```

LANG=C **top** -E k
while true; do clear;head -n 27 **/proc/meminfo**;sleep 2;done
while true;do clear;**free**;sleep 2;done

```
alongside each other (see the attached screenshot from Ubuntu 22.04.3 LTS), I can see which numbers match (at least approximately), and I can see how

**[FONT=Courier New]vmstat -s[/FONT]**

fits into it too, except that I can't see **[FONT=Courier New]available memory[/FONT]**.

In the output I should look for data names containing '**[FONT=Courier New]avail[/FONT]**', when things are getting tight.

[hr][/hr]
But, I still don't understand what **[FONT=Courier New]htop[/FONT]** is displaying on the

**[FONT=Courier New]Mem[|||   2.5G/126G][/FONT]** line (in MAFoElffen's output).

My conclusion must be that **[FONT=Courier New]htop[/FONT]** is useful in many ways, but not in order to monitor the usage of RAM, when things are getting tight.

---

### Post by MAFoElffen on 2023-11-18
You know I thrash my workstation testing lots of things at one. I keep an eye on things at a glance by using conky to display stats on my desktop. CPU. Memory, processes, temp's, etc.

---

### Post by ajgreeny on 2023-11-18
> **MAFoElffen said:**
> You know I thrash my workstation testing lots of things at one. I keep an eye on things at a glance by using conky to display stats on my desktop. CPU. Memory, processes, temp's, etc.
Exactly what I've done for many years and find it incredibly useful especially when messing about running VMs in KVM/QEMU when usage tends to go very high of course.
It is so very informative that I feel a bit lost without that when I have to use other computers and they're running slowly.

---


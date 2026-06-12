---
title: "CPU's IO Wait"
date: 2007-09-08
forum: General Help
---

### Post by bobshowrocks on 2007-09-08
Recently, after the latest Kernel update, Ubuntu runs much slower. The GNOME system monitor that can be placed on a panel shows an excessive amount of IO wait from the CPU.  Even when I let the computer sit for several minutes it will still show the CPU spiking up to 100% from IO Wait. The list of processes and the top program don't show anything using the CPU during these spikes. This has the effect of not allowing programs to respond, but the mouse movements and clock stay in sync.

Is this a common problem? I haven't done a fresh install since Dapper Drake, is a install be the best fix for this?

---

### Post by phiphi on 2007-11-10
I have the same Problem
Ubuntu64, Gnome

---

### Post by antares8 on 2007-11-16
I have the same problem all the time!

When copying files or launching ```
stress --hdd 1
``` the iowait explodes - which is really annoying as the system gets very slow.

Any suggestions? I am running gutsy with the latest generic kernel. DMA is activated:

```
hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   2384 MB in  2.00 seconds = 1193.12 MB/sec
 Timing buffered disk reads:  148 MB in  3.01 seconds =  49.23 MB/sec
```

Any help appreciated!

---

### Post by Alterios on 2007-11-21
What version of Ubuntu are you using? I was having this problem in Gutsy until I uninstalled Tracker and the associated files. After I killed the Tracker proccess my IOWait dropped from 90% to 0%. My HDD light stopped running for the first time since I installed it.

---

### Post by mhossom on 2007-11-21
I recently upgraded from Feisty to Gutsy and I have been having the same issues.  Applications take much longer to load and seem to hang half way through the process.  I did not experience any of these problems with Feisty.

Please help.  I am trying to persuade my wife to give up on M$.  If she happens to try this laptop before I can fix this, I'm sunk :(

---

### Post by 00ber n00b on 2007-11-22
my cpu monitor shows a spike every 10-15 seconds, I did notice the tracker taking up some of the cpu power, but it didn't seem like it was hurting anything.  I'm gonna try and un-install tracker to see if it helps.

---

### Post by mhossom on 2007-11-23
> **00ber n00b said:**
>   I'm gonna try and un-install tracker to see if it helps.

I removed Tracker and it seems to have helped.  I am not surprised that a single app caused this on my laptop.  It is an older laptop with with a mere 384 MB of RAM.

---

### Post by foehawk on 2007-12-31
I am having the same problem, what with the CPU I/O spikes. I uninstalled Tracker to see if that would help, but it did not. I've been searching the forums and google, but I haven't discovered a working solution.

I'm running Ubuntu Gutsy (7.10) on a notebook with specs:
Intel Centrino 2.00 GHz - Mobile Intel 915GM/GMS/910GML Express Chipset
1 GB DRAM

Any help would be greatly appreciated.

---

### Post by dcstar on 2007-12-31
> **bobshowrocks said:**
> Recently, after the latest Kernel update, Ubuntu runs much slower. The GNOME system monitor that can be placed on a panel shows an excessive amount of IO wait from the CPU.  Even when I let the computer sit for several minutes it will still show the CPU spiking up to 100% from IO Wait. The list of processes and the top program don't show anything using the CPU during these spikes..........

In System Monitor, turn on:

View-All Processes
Edit-Preferences and select CPU Time

That may show more usable info when the issue occurs.

BTW, are you using Compiz effects? (if so, turn them off).

---


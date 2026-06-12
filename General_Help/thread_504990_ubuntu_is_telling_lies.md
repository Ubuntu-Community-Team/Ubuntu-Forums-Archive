---
title: "ubuntu is telling lies"
date: 2007-07-19
forum: General Help
---

### Post by lord lewix on 2007-07-19
hi..
my computer has 2.5gb of ram yet ubuntu says it has 1.5gb and same prob with my hard drive i have 500gb yet ubuntu says i have 100gb cant solve problem...:confused:

---

### Post by lisati on 2007-07-20
There are a number of possibilities, which include:[LIST=1]
[*]There are different ways of measuring what constitutes a Gigabyte and what constitutes a megabyte. Some definitions are based on 1000 (as in science) and some are based on 1024 (as in computers). These on their own, however, don't account for all of the differences
[*]Have your BIOS or some other settings been messed up?
[*]What else do you have loaded on your computer?
[/LIST]
Perhaps some user more knowledgable than myself might be able to help with appropriate commands to run from the command line.

---

### Post by ADT on 2007-07-20
Ubuntu is giving you a big difference from what you really have.
What program is giving you that information?

Some commandline programs you can use for seeing your RAM and Drive resources are:

df - reports file system disk space usage.
vmstat - reports virtual memory statistics.
free - Display amount of free and used memory in the system.

Open a terminal emulator. I think its in applications>system>terminal.
Type into the terminal:

```
df -m
```
then
```
vmstat
```
then
```
free -m
```

Compare the results with what you know.

My system:
```
df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda5                 3755      **1468      2097**  42% /
none                        93         0        93   0% /dev/shm
/dev/sda1                   38         9        27  26% /boot
/dev/sda3                10045     ** 2766      6769**  30% /home

```

Numbers in bold are disk space in MegaBytes.

```

vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0   **8084**   8744  80232    0    0    14     7   35  253  6  1 93  0

```

Numbers in bold are RAM that is free (in KBs).

```

free -m
             total       used       free     shared    buffers     cached
Mem:           185        177          7          0          8         78
-/+ buffers/cache:         90         94
Swap:          267          0        267

```

All these numbers are MBs.

---

### Post by punong_bisyonaryo on 2007-07-20
Hmm, thats weird. Says here I have 5mb free

```
jeff@carbon:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           487        482          5          0          2        308
-/+ buffers/cache:        171        316
Swap:          713        156        557
```

but a look at the System Monitor says:
174.8MiB of 488.0Mib

Am I missing something? Isn't System Monitor supposed to be reporting the same thing as free?

---

### Post by ADT on 2007-07-21
Thats weird. What does vmstat say?

I think in linux that when RAM is used by an application and then the application is closed the RAM that should be freed is not actually free but waiting to be used again. i.e. your system may say that you have no RAM free but you will notice no performance loss.

Maybe the gnome system monitor takes this ( free RAM but not completely freed ) into account and displays it as free.

This is just my ramblings on how I think RAM in linux works. Hopefully some one can explain how it works, better and correctly.

---

### Post by punong_bisyonaryo on 2007-07-21
Actually that's the readout when I was running Windows XP in a vmware player with 192mb memory allocated to it. Hmm, I hope anyone out there who knows about this, please explain this to us.

---

### Post by bapoumba on 2007-07-21
> **punong_bisyonaryo said:**
> Hmm, thats weird. Says here I have 5mb free

```
jeff@carbon:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           487        482          5          0          2        308
-/+ buffers/cache:        171        316
Swap:          713        156        557
```

but a look at the System Monitor says:
174.8MiB of 488.0Mib

Am I missing something? Isn't System Monitor supposed to be reporting the same thing as free?
This comes from the system units used to show the memory (powers of 10 vs powers of 2):
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/123932]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/123932")
[http://bugzilla.gnome.org/show_bug.cgi?id=301838]("http://bugzilla.gnome.org/show_bug.cgi?id=301838")

There has been a very long discussion on the -devel-discuss mailing list too:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-June/001094.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-June/001094.html")

Edit: BTW, I moved the thread to "General Help".

---

### Post by ADT on 2007-07-21
Thank you for the links. It makes sense now.

---

### Post by bapoumba on 2007-07-21
You're welcome :)
Subscribing to the -devel and -devel-discuss mailing list (-devel list got split not so long ago) is a good idea. I've been subscribed from a very long time, when I could just understand a few words in each mails. It's a good education source, if you are curious enough to look around for the obscure stuff.

---

### Post by punong_bisyonaryo on 2007-07-31
Actually, that wasn't what I was pointing out. System Monitor says I'm using 174.8MiB of ram. In free, on the Mem line it says 482 (MiB or MB wouldn't matter with a discrepancy this big) used. Should I read from the buffers/cache line instead? Why? I don't understand.

PS Sorry took me a week before I got to reply.:)

---

### Post by zorkerz on 2007-10-24
[LEFT]not sure anyone is around here but i just noticed something odd with system monitor.

I have a core 2 due processor and it has been reporting both cpus steadily around 50% now in the resources tab.

However in the processes tab it shows no precesses over 15 percent (system monitor itself) and all others are reported just about 0 most of the time. 

What causes this?  If i add up all the percents in precesses ta
[/LEFT]

---


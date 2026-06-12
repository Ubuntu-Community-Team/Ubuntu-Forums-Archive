---
title: "Compiz fusion and fusion icon gradually eating CPU time"
date: 2008-05-04
forum: General Help
---

### Post by earthforce_1 on 2008-05-04
I have reposted this from Desktop Environments as it more properly belongs here - apologies if there is an easier or more properly way to do this, I don't know.  I have filed a bug report about this shortly before 8.04 was released, but there has been no activity on it.

I have a P4 3.6 GHz with 2 G of RAM, and a G-Force 6600 with 512M of ram, and during the late alphas and early Hardy betas, compiz fusion ran just fine. The desktop cube worked great, effects were smooth, etc. At some point shortly before release there was an update that causes compiz fusion (or the compiz fusion icon) to start consuming all of the CPU cycles. After a while, virtually everything on the desktop becomes slow and stuttered as either the compiz or fusion-icon starts consuming most or all of the available CPU time. Restarting the desktop via the fusion icon makes it go away for a while, until something makes it jump back up. If top reports fusion-icon itself is the culprit then I have to kill its PID from a command line prompt. When the system starts running its screensaver, the problem is guaranteed to appear - after a while, the screensaver itself shows signs of CPU loading by running stuttered.

I really love the desktop cube, but it is very annoying to be constantly killing processes or restarting the desktop every 20 minutes or so. This was working perfectly just before release, and was somehow busted in a last minute update. Was the threading model changed? I am not doing anything when the CPU is burning away like that, so I can't imagine why compiz is being such a CPU hog when the desktop is idle.

here is what top reports (If I leave it alone, CPU load eventually reaches 100%!):
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
525 user 20 0 61668 43m 11m R 52 2.1 24:01.58 compiz.real
495 user 20 0 40780 25m 9m S 28 1.3 12:49.14 fusion-icon
7121 user 20 0 334m 227m 28m S 4 11.2 88:44.01 firefox
6938 root 20 0 193m 93m 39m S 3 4.6 329:38.64 Xorg
7120 user 20 0 7808 4932 1924 S 1 0.2 72:23.85 gconfd-2
21089 user 20 0 85128 23m 11m R 1 1.2 0:31.88 gnome-terminal
6319 root 15 -5 0 0 0 S 0 0.0 1:34.37 kondemand/0
7232 user 20 0 39984 7596 3816 S 0 0.4 43:45.88 pulseaudio
7251 user 20 0 16556 6440 4900 S 0 0.3 5:45.62 gnome-screensav
7419 user 20 0 93908 75m 9m S 0 3.7 101:20.96 multiload-apple
22374 user 20 0 171m 71m 39m S 0 3.5 4:11.62 totem
29164 user 20 0 184m 66m 22m S 0 3.3 24:53.82 rhythmbox
1 root 20 0 2844 1688 544 S 0 0.1 0:01.16 init
2 root 15 -5 0 0 0 S 0 0.0 0:00.00 kthreadd
3 root RT -5 0 0 0 S 0 0.0 0:00.04 migration/0
4 root 15 -5 0 0 0 S 0 0.0 1:38.86 ksoftirqd/0
5 root RT -5 0 0 0 S 0 0.0 0:00.52 watchdog/0

After I restart the desktop via fusion-icon

Tasks: 135 total, 1 running, 132 sleeping, 0 stopped, 2 zombie
Cpu(s): 16.0%us, 1.8%sy, 0.0%ni, 81.8%id, 0.0%wa, 0.0%hi, 0.5%si, 0.0%st
Mem: 2075520k total, 1967064k used, 108456k free, 253764k buffers
Swap: 6080560k total, 38324k used, 6042236k free, 810516k cached

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
495 user 20 0 41456 26m 10m S 21 1.3 14:25.26 fusion-icon
6938 root 20 0 199m 94m 40m S 5 4.7 329:52.65 Xorg
7121 user 20 0 334m 227m 28m S 3 11.2 89:15.01 firefox
1981 user 20 0 50924 32m 11m S 3 1.6 0:03.52 compiz.real
21089 user 20 0 85348 23m 11m S 1 1.2 0:32.28 gnome-terminal
1988 user 20 0 18568 9948 6940 S 1 0.5 0:00.72 gtk-window-deco
7120 user 20 0 7808 4932 1924 S 1 0.2 72:25.99 gconfd-2
7232 user 20 0 39984 7596 3816 S 1 0.4 43:47.84 pulseaudio
7253 user 20 0 53984 26m 14m S 1 1.3 17:53.19 gnome-panel
7419 user 20 0 93908 75m 9m S 1 3.7 101:22.96 multiload-apple
22374 user 20 0 171m 71m 39m S 1 3.5 4:12.43 totem
7251 user 20 0 16556 6444 4900 S 0 0.3 5:46.47 gnome-screensav
1 root 20 0 2844 1688 544 S 0 0.1 0:01.16 init
2 root 15 -5 0 0 0 S 0 0.0 0:00.00 kthreadd
3 root RT -5 0 0 0 S 0 0.0 0:00.04 migration/0
4 root 15 -5 0 0 0 S 0 0.0 1:38.94 ksoftirqd/0
5 root RT -5 0 0 0 S 0 0.0 0:00.52 watchdog/0

Now, after I kill fusion-icon from the command line and restart it:
Tasks: 135 total, 1 running, 132 sleeping, 0 stopped, 2 zombie
Cpu(s): 6.2%us, 1.4%sy, 0.0%ni, 92.3%id, 0.0%wa, 0.2%hi, 0.0%si, 0.0%st
Mem: 2075520k total, 1957888k used, 117632k free, 253804k buffers
Swap: 6080560k total, 38324k used, 6042236k free, 810480k cached

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
7121 user 20 0 334m 227m 28m S 6 11.2 89:21.35 firefox
1981 user 20 0 51984 33m 11m S 2 1.7 0:07.16 compiz.real
6938 root 20 0 199m 95m 39m S 1 4.7 329:58.13 Xorg
2018 user 20 0 30108 14m 8708 S 1 0.7 0:00.28 fusion-icon
7120 user 20 0 7808 4932 1924 S 1 0.2 72:26.47 gconfd-2
7232 user 20 0 39984 7596 3816 S 1 0.4 43:48.38 pulseaudio
7419 user 20 0 93908 75m 9m S 1 3.7 101:23.60 multiload-apple
22374 user 20 0 171m 71m 39m S 1 3.5 4:12.70 totem
7217 user 20 0 2828 1384 876 S 0 0.1 20:36.60 dbus-daemon
1 root 20 0 2844 1688 544 S 0 0.1 0:01.16 init
2 root 15 -5 0 0 0 S 0 0.0 0:00.00 kthreadd
3 root RT -5 0 0 0 S 0 0.0 0:00.04 migration/0
4 root 15 -5 0 0 0 S 0 0.0 1:38.94 ksoftirqd/0
5 root RT -5 0 0 0 S 0 0.0 0:00.52 watchdog/0
6 root RT -5 0 0 0 S 0 0.0 0:00.04 migration/1
7 root 15 -5 0 0 0 S 0 0.0 0:07.16 ksoftirqd/1
8 root RT -5 0 0 0 S 0 0.0 0:00.56 watchdog/1

After anywhere from 20 minutes to an hour I will see a vampiric leeching of my CPU, courtesy of compiz until it hits 100% and the desktop is so sluggish you would swear I am running on a 386 with minimum RAM.  If the screensaver kicks in, the CPU is certain to be fully loaded when you exit the screensaver, the only cure is to manually reload the desktop and/or exit and restart the fusion icon process itself.

---

### Post by tvtech on 2008-05-04
compiz-fusion absorbs my cpu the second I enable desktop FX I can barely use my computer at all it's wonderful it reminds me of windows me

---

### Post by Hammer89 on 2008-05-04
Working great for me so far... running Ubuntu on a Toshiba A135-S2386, ATI Xpress 200m GPU, 1.73Ghz dual core processor, 2Gb ram.. no real complaints so far. :D

---

### Post by growlf on 2008-10-25
I am having the same issue - but it seems to come and go.   Occasionally a reboot or switching to "failsafe gnome"  session temporarily fixes  it. Not liking this. 

I am  using Ubuntu 8.04 and  this was  not  an issue when  I was  using Ubuntu 7 - not  sure  that is related though.

---

### Post by borlosky on 2008-11-12
i had similar issue with bicubic filter turned on, so i turned it off, and now seems to be more stable as far as cpu usage is concerned.

---

### Post by Izek on 2008-11-12
> **borlosky said:**
> i had similar issue with bicubic filter turned on, so i turned it off, and now seems to be more stable as far as cpu usage is concerned.

Too bad mine's off by default, so that won't help me get by the nasty cpu issues.

---

### Post by borlosky on 2008-11-12
> **Izek said:**
> Too bad mine's off by default, so that won't help me get by the nasty cpu issues.

:(

---

### Post by Izek on 2008-11-12
I reported a bug about it for my driver, but we'll see if they decide to keep it active, or let it expire.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/296497](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/296497)

---

### Post by tarahmarie on 2008-11-19
Ditto.  compiz.real is eating up one of my cores full time at 100%.

---


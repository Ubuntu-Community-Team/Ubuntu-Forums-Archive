---
title: "System freezes immediately on suspending, where do I investigate?"
date: 2020-02-13
forum: General Help
---

### Post by kinite4067 on 2020-02-13
I've been trying to suspend my newly installed Xubuntu 19.10 machine, a Lenovo S340 Ideapad. Upon pressing suspend while logged in, the system freezes instantly. The screen does not go black and even after half an hour, the machine accepts no inputs other than the classic REISUB combo. I can't even move the mouse or change tty. This happens whenever I attempt to suspend, even with *systemctl suspend*.

**Where can I investigate the cause of this problem?** kern.log shows the entry* PM: suspend entry (deep)* at what looks like the appropriate time, but nothing comes before this other than what I was doing many minutes before and nothing comes after until the reboot has started. On the other hand, syslog.log shows more activity, and I have reproduced this below. Everything before and after the given point in time is too far out to be relevant:
```

Feb 12 22:55:17 MyPC NetworkManager[1198]: <info>  [1581548117.3612] device (p2p-dev-wlp2s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Feb 12 22:55:17 MyPC whoopsie[1521]: [22:55:17] offline
Feb 12 22:55:17 MyPC NetworkManager[1198]: <info>  [1581548117.3616] manager: NetworkManager state is now ASLEEP
Feb 12 22:55:17 MyPC systemd[1]: Reached target Sleep.
Feb 12 22:55:17 MyPC systemd[1]: Starting Suspend...
Feb 12 22:55:17 MyPC kernel: [ 8812.324175] PM: suspend entry (deep)
Feb 12 22:55:17 MyPC systemd-sleep[16039]: Suspending system...
```

As for solving this problem, nothing that I've seen online has worked:
[LIST]
[*]Blacklisting Intel modules such as mei has changed nothing. 
[*]I have no NVDIA modules to blacklist 
[*]cat /sys/power/mem_sleep returns s2idle [deep] as expected 
[*]Making changes to Grub's GRUB_CMDLINE_LINUX_DEFAULT settings for the PCIe connection to my SSD has done nothing. 
[*]Editing SuspendState in /etc/systemd/sleep.conf has done nothing. 
[/LIST]

EDIT: Problem was mysteriously fixed by the 20.04 upgrade.

---

### Post by ajgreeny on 2020-02-13
Just out of interest, what happens if you use the command ```
xfce4-session-logout --suspend
```
It certainly works as it should in 20.04 to suspend the OS, so I assume it will in 19.10, provided your problem is not hardware related.

---

### Post by kinite4067 on 2020-02-13
> **ajgreeny said:**
> Just out of interest, what happens if you use the command ```
xfce4-session-logout --suspend
```
It causes a freeze after I hit enter. The last thing that happens is the line break appearing on the terminal.

---

### Post by kinite4067 on 2020-02-15
Just a thought, are there any signs of this being fixed in 20.04?

---

### Post by kinite4067 on 2020-02-17
Another thought - probably my last - wasn't the kernal code for sleep changed a few years ago? IIRC pm-utils isn't used for suspend any more either. Is there a chance that my problems would be solved if I tried an old Live CD from 16.04?

---

### Post by ra7411 on 2020-02-17
It may be that the kernel version you're using is botching suspend/wakeup with your hardware.
See if 'ubuntu kernel update utility" works on your system. Note what kernel you're using, try some others and see if s/w problems go away.

---

### Post by kinite4067 on 2020-02-18
> **ra7411 said:**
>  'ubuntu kernel update utility"
That's 'sudo apt-get install ukuu', right? Should I backup before playing with this stuff? It doesn't sound easily revertible.

---

### Post by kinite4067 on 2020-02-18
According to ukuu, I'm running the 5.3.0-29-generic kernel. Any idea what I should try instead? 5.3.18 is the latest point update, is that what I should go for?

---

### Post by ra7411 on 2020-02-18
OK, your last post came in while I was typing the stuff below.
In my UB 18.04 desktop, I had s/w failures in kernels 5.5.xxx and   5.3.xxx, I randomly tried 5.1.0-050100-generic and s/w has been working for the last 4 days.
Good luck.

xxx
Using this utility to change kernel versions you boot with is less dangerous than it seems.
However, ALWAYS have o/s and user files backed up.
Use the utility to get some kernel versions onto to your machine.
I'm not familiar with Xubuntu.  
From recent personal experience in Ubuntu 18.04, during bootup,  select -[COLOR=#333333][FONT=&amp]Advanced Options- and you get a list of kernels to use
.
Paper and pencil- take notes, see if any of these kernels work in allowing suspend/wakeup to work.

Kernels do have some security features in them, but I doubt using older kernels (as you might wind up using) on a linux pc v.  linux [/FONT][/COLOR][COLOR=#333333][FONT=&amp]server[/FONT][/COLOR][COLOR=#333333][FONT=&amp] will be particularly hazardous.



[/FONT][/COLOR]

---

### Post by kinite4067 on 2020-02-18
> **ra7411 said:**
> I had s/w failures in kernels 5.5.xxx and   5.3.xxx, I randomly tried 5.1.0-050100-generic and s/w has been working for the last 4 days.
Good luck.
No luck I'm afraid, after installing a bunch of new ones, I've tried most of the following kernels:
[LIST]
[*]5.1.21-050121.201907280731
[*]5.3.0-18.19+1
[*]5.3.18-050318.201912181133
[*]5.3.0.29.33
[*]5.3.0-29.31
[*]5.0.21-050021.201906040731
[*]5.1.1-050101.201905110631
[/LIST]
And I've had identical failures in each one. Any ideas for my next step?

---

### Post by ra7411 on 2020-02-18
> **kinite4067 said:**
> No luck I'm afraid, after installing a bunch of new ones, I've tried most of the following kernels:
[LIST]
[*]5.1.21-050121.201907280731
[*]5.3.0-18.19+1
[*]5.3.18-050318.201912181133
[*]5.3.0.29.33
[*]5.3.0-29.31
[*]5.0.21-050021.201906040731
[*]5.1.1-050101.201905110631
[/LIST]
And I've had identical failures in each one. Any ideas for my next step?

I'm using an AMD machine, I think you're on an Intel - that could affect things. 
[COLOR=#000000]Lenovo S340 Ideapad has a touchscreen? ---- maybe that's creating a complication..
[/COLOR]
At the moment, the only thing that comes to mind is to inspect your bios for anything that might pertain to s/w.
Did  your machine come with some manfacturer's presets?

TRY google search on "Lenovo suspend wake up problems" - you might get an idea re. drivers, power mgt, bios that cures this thing.

---

### Post by kinite4067 on 2020-02-18
Assuming that we've ruled out kernel and BIOS options, are we left with nothing but editing grub? I'm surprised that there's no other log files that I can look at.

> **ra7411 said:**
> I'm using an AMD machine, I think you're on an Intel - that could affect things. 
I am.
> [COLOR=#000000]Lenovo S340 Ideapad has a touchscreen? ---- maybe that's creating a complication..
[/COLOR]Mine doesn't.
> At the moment, the only thing that comes to mind is to inspect your bios for anything that might pertain to s/w.
I've had a look, nothing there seems relevant.
> Did  your machine come with some manfacturer's presets?
In the BIOS? Yeah, although none of them look relevant and many have been disabled anyway. Elsewhere? My only storage is a fresh SSD that, to my knowledge, was totally blank before I put Xubuntu on it.
>  TRY google search on "Lenovo suspend wake up problems" - you might get an idea re. drivers, power mgt, bios that cures this thing.
Nothing that I saw helped. In fact, the one thing that I found on the ArchWiki caused more problems.

---

### Post by ra7411 on 2020-02-18
The best option is probably to power down and bootup instead of suspend/wakeup. You have an ssd with the o/s on it (I think) so bootup should be fairly fast. Do many power cut offs to get out of a dead screen will eventually botch your install.

---

### Post by kinite4067 on 2020-02-19
Ideally, I'd like to fix the problem. Do you know anywhere else that I can ask for help?

---

### Post by ra7411 on 2020-02-19
> **kinite4067 said:**
> Ideally, I'd like to fix the problem. Do you know anywhere else that I can ask for help?

Lenovo forum(s) - but they probably won't have any familiarity with linux ubuntu o/s.

---


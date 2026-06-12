---
title: "why run  baloo file process when not requested"
date: 2019-10-09
forum: General Help
---

### Post by bjngchn on 2019-10-09
I try to run chrome, it doesn't work, and it turns into a zombie 
on the panel, which can't be moved/maximized/minimized/closed ,... etc, although there are such options on it. 
and a baloo file process runs. I didn't want such a process to run. 
It is like I can't do what I want, but someone is trying to do something I don't want.

Any possible reasons, cures, and harmless tests which I can try?

---

### Post by TheFu on 2019-10-09
What is "baloo?"  Only reference I find is related to _The Jungle Book_.

---

### Post by deadflowr on 2019-10-09
> **TheFu said:**
> What is "baloo?"  Only reference I find is related to _The Jungle Book_.

Chuckle chuckle.

baloo is kde's file indexer.
In system settings go to Search and turn it off.
or from terminal
```
balooctl disable
```
check status with
```
balooctl status
```

Though I'm not sure if disabling through terminal is permanent.
(As to whether or not it persists on reboots
System setting should be persistent though.)

---

### Post by Holger_Gehrke on 2019-10-09
I assume you're running KDE ? Then [baloo]("https://wiki.archlinux.org/index.php/Baloo") should be the indexer for the search facility. Since chrome is supposedly even more hungry for memory than Firefox and I've had ff become unresponsive when memory was low, check the output of 'free' in a terminal when chrome hangs. Might be it's going to swap and just needs some time. Reading between the lines in various posts about baloo on the net, it seems to use a lot of memory and cpu, too. What amount of memory is available on your machine ?

Holge

---

### Post by bjngchn on 2019-10-09
Thanks to all.  Yes, probably using KDE. 
Just after posting this system settings stopped working. After disabling baloo, system settings started to work.  
Chromium seems to increase memory usage by 1 percent.  
When I type chromium on command line, I get command not found error.
When I click on Chromium on the panel or desktop, it runs on the panel outsie my control. 
When I do ps ux, I see  6 processes  involving chromium, namely things running under /usr/bin/chromium-browser  --enable-pinch 
and similar ones. 
This bug was created just after when I was trying ot fix things using system settings, 
and there I disabled kwallet. I hate it when chromium shows me kwallet after each step.


I wonder what is the meaning of an application running but staying on the panel and being  unreachable for me. 
Does this mean some dependencies were disabled, or is memory not enough etc ..

---

### Post by TheFu on 2019-10-09
Ah, that explains it.  Not using a DE makes things like that not happen.  Still rocking fvwm here.  I have different issues, but memory use and CPU from unknown processes ain't one.

---

### Post by bjngchn on 2019-10-10
So what is the alternative to K/DE and how can it be installed. I mean,  does it need to be done during kubuntu installation, or is it a softer change, like a small change in system settings?

---

### Post by bjngchn on 2019-10-10
Fixed after nautilus reinstall command here:

[https://ubuntuforums.org/showthread.php?t=2247343](https://ubuntuforums.org/showthread.php?t=2247343) 

(baloo is not the problem, but I had suspected it was part of the problem)

---

### Post by TheFu on 2019-10-10
> **bjngchn said:**
> So what is the alternative to K/DE and how can it be installed. I mean,  does it need to be done during kubuntu installation, or is it a softer change, like a small change in system settings?

There are at least 50 different DEs and about 15 are fairly popular.  [https://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available](https://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available) is one answer, but from 2017.  There is a writeup about them in these forums earlier this year.

The GUI is just another program.  You don't need to be tied to it if it doesn't fit your needs.  Most people like an all-in-one installed DE and programs since they don't know what they like yet.  I've been around a really long time. I know which programs I want and don't want installed. Almost always, I find any full DE to be bloated.  I don't use bluetooth. I don't use network-manager, I don't need/want any menus or a panel. I don't want to worry when Canonical decides to change everything about the GUI anymore, so I use a GUI that I've been using since 1995.  It isn't for most people, since configuration is controlled via text files. There is no GUI for that.  No background processes are magically run to make my life easier that I didn't setup.  I have a few that I definitely DO want.

Normally, I send people really new to Linux here:  [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) to read about important things, like DEs. 

A DE is optional for any GUI.  A WM is required.  fvwm is a WM.  I haven't looked at KDE since around 2003, so I don't know about the brilliant and stupid things it has today.  fvwm sucks sometimes too.  <Alt>-tab doesn't work as anyone would expect. Your goal is to find a DE/WM that you sorta like, that isn't too heavy on your PC, that doesn't get in the way for getting things done.  Well, that's my goal.

---


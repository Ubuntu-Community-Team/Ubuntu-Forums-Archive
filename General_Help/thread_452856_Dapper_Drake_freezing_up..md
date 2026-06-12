---
title: "Dapper Drake freezing up."
date: 2007-05-23
forum: General Help
---

### Post by theDaveTheRave on 2007-05-23
Hi all.

I am sure that there must be a thread out there with this topic allready in discussion but I've been looking for hours and no-one seems to have the same problem as me!

It would seem that when I am using a large number of applications (bad habit!) that after a while Dapper will simply die on me, I may or may not have a mouse pointer.Also the HDD seems to be accessing a lot (but i do have 2 HDD so it could be either)

I suspect I am running out of memory! or similar?

Anyway what i would like to do is to open a terminal and terminate a number of the processes, but I can't even do that.

Is there a way that I can "log out" and back in to a non-gui and perform the desired operations so as not to have to perform a << <ctrl alt sysrq> S U B >> to reboot the whole system.

I haven't been able to pin it down to a specific activity, and i don't know what log files I should look at.

I did look at var log messages, but there seems to be no details of a why the freeze would have occurd.

Is it possible to have TOP running in the background and then saved to a file when I do the reboot, so as i can then see if it is a memory issue?

your help is really appreciated.

thanks in advance.

---

### Post by dbott67 on 2007-05-24
You can try some of the following options:

1. Press **CTRL-ALT-F1** to get to a terminal
2. Run a terminal program like **tilda** or **yakuake**:
```
dbott@feisty:~$ [COLOR=Red]sudo apt-cache search yakuake[/COLOR]
yakuake - a Quake-style terminal emulator based on KDE Konsole technology
dbott@feisty:~$ [COLOR=Red]sudo apt-cache search tilda[/COLOR]
tilda - Linux terminal which behaves like terminals in shooter games

```
Both of these terminals can be "pulled down" by pressing a key (like the '~' key).  If you can get the terminal to open, you could then dump the output of 'ps -aux' to a file:
```
ps -aux > processes.txt
```
```
free -o -m > ram-memory.txt
```

I'm sure that there are other more elegant solutions, but those are just off the top of my head.

-Dave

---


---
title: "More options to shedule and postpone update reboot."
date: 2019-10-04
forum: General Help
---

### Post by jasper99 on 2019-10-04
There are only 2 options, Restart later and restart now.

I want to have that there are more options, a postpone function te postpone forspecific time for example, 2 hour, 3 hour...
And a shedule option to add a time the computer go to restart.
A option to auto restart after doing updates. If a reboot is needed.


[IMG]https://www.tecmint.com/wp-content/uploads/2016/04/Restart-to-Finish-Ubuntu-Updates.png[/IMG]

---

### Post by mikewhatever on 2019-10-04
You can easily schedule restarts with the <shutdown> command:

```

sudo shutdown -r +120 #reboot after 2 hours
sudo shutdown -r 2:00 #reboot at 2:00AM

```

I don't think the Update Manager has that kind of feature.

---

### Post by jasper99 on 2019-10-05
there even is a option to mute that message.
That repeat on sereral minutes.

And what is the shutdown command to PM?

---

### Post by deadflowr on 2019-10-05
> And what is the shutdown command to PM?
It runs a 24hr clock, so 2:00PM would be 14:00

---

### Post by jasper99 on 2019-10-10
> **mikewhatever said:**
> You can easily schedule restarts with the <shutdown> command:

```

sudo shutdown -r +120 #reboot after 2 hours
sudo shutdown -r 2:00 #reboot at 2:00AM

```

I don't think the Update Manager has that kind of feature.

But that don't mute the message?

---

### Post by TheFu on 2019-10-10
I find it easier to just remove automatic checking for updates and manually run them every Saturday morning from a terminal.  
If the updates are allowed to the APT DB, the nags begin with most DEs.  We have to stop the updates for the APT DB to prevent those.

How to stop all that depends on the specific version and DE used.

---

### Post by jasper99 on 2019-10-11
What is APT DB and DE??

Apt database? and ......???

If do manual then i do not have almost the latest updates. On Windows i install never updates because that hostage updates system irritating me very much. therefore that i have completed turned off all of the updates. nice and quiet, sleep well!
[IMG]https://www.computable.nl/img/57/59/org_org/5759283.jpg[/IMG]

---

### Post by TheFu on 2019-10-11
> **jasper99 said:**
>  
If do manual then i do not have almost the latest updates.

Not true.
```
sudo apt update
sudo apt upgrade

```
Once every other week or so, run 
```
sudo apt autoremove
sudo apt autoclean
```

If you want to move from 18.04.3 --> 18.04.4 keeping the same kernel, use 
```
sudo apt dist-upgrade
```
It will never change from 18.04.x to any other release.  
If you want to get the HWE kernels, those have to be manually requested. There are usually specific instructions, since changing kernels like that usually means changing GPU drivers and lots of libraries too.

APT has a database.  Any tool that works with the Ubuntu package management system, works with it or uses lower-level tools to work with it.

DE - Desktop Environment.  [https://en.wikipedia.org/wiki/Desktop_environment](https://en.wikipedia.org/wiki/Desktop_environment) Somehow you've missed some basic knowledge for Linux. Read this: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) to fill in some of the most important, day-1 information.

WM - Window Manager.  [https://en.wikipedia.org/wiki/Window_manager](https://en.wikipedia.org/wiki/Window_manager)

Good on you for asking about that aren't understood.  Nobody knows this stuff in the beginning.  Don't be afraid to use a wiki-search since most of these things are well covered their and reading just the first few paragraphs might be all you need.

If a computer is on any network, it really needs to be patched.

---

### Post by jasper99 on 2019-10-13
I mean directly, if i do manual weekly the updates can be some days later then they released.

---

### Post by TheFu on 2019-10-13
> **jasper99 said:**
> I mean directly, if i do manual weekly the updates can be some days later then they released.

And you don't get the 1 in 40 patches that has to be redo because the original issue wasn't completely solved.  I've been patching weekly, on weekends for about 20 yrs.  There have been a few high-risk problems for specific servers I run which I've patched 1 day after release.  It is always a trade off between stability, uptime, and security risks.

New is the enemy of stable.

---


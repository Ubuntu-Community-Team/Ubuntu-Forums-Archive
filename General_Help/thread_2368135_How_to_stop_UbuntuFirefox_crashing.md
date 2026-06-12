---
title: "How to stop Ubuntu/Firefox crashing ?"
date: 2017-08-07
forum: General Help
---

### Post by oisin000 on 2017-08-07
Hi, 

I haven't used Linux for ~15years but from my previous experience one of the nice features was that, unlike Windows, when  program crashed I could simply launch a terminal and kill the process. I have been using Ubuntu for months now and unfortunately it now behaves like Windows; Firefox crashes and it takes the whole system down with it, I generally have no alternative other than yanking the power cable and rebooting. I'm running Ubuntu 14.04 LTS on a Dell Latitude E6410 with 4Gigs of RAM. In general when the problem arises the only program I will have running is Firefox (and maybe a terminal in the background). Firefox will have 20+ tabs open and I will notice that the disk-access LED will become permanently lit. The mouse will become very sluggish and then totally unresponsive. Sometimes if I am quick and hit CRTL-ALT-T while the mouse is still responding I can launch a terminal and try to kill Firefox or hit CTRL-ALT-M (shortcut to xkill) and click on the Firefox to kill it and then the system survives, Generally though this is not successful and I am left with permanent disk-access (as indicated by the LED) and both the keyboard and mouse are unresponsive; I cannot launch any other programs to try to kill Firefox. So, does anyone know what might be causing this or how I might fix or mitigate it ? 
Is it possible to run programs (Firefox) in some sort of 'limited mode', so that it would not be possible for it to hijack all system resources when it crashes ? Then I could be sure that launching a terminal or hitting CTRL-ALT-M would be an effective way of dealing with the problem.  
Are there any other suggestions as to how to deal with this behaviour ? 
I am currently on version 54.0 (64 bit) of Firefox, but this has been going on for ~6months so I'm sure it affects many versions of Firefox and indeed the fact that it happens with so many versions over time makes me wonder if there is not something in the underlying Ubuntu system that is responsible rather than Firefox. It does seem very odd that permanent disk access prevents other commands from running, I mean if I issue CTRL-ALT-T to launch a terminal should this not be going directly to the CPU ? Why would Firefox monopolizing the the disk be preventing the CPU responding to keyboard commands ?

Thanks, 

Usjes.

---

### Post by dragonfly41 on 2017-08-07
I moved from Firefox usage to Chromium Web Browser but still experience freezes from time to time (as do many others if you browse the forum for "freezes")..
When I was using Firefox with many tabs open I investigated Tab Groups Helper extension including dabbling with its software.   It was a nice extension and tabs can be put into sleep mode avoiding too much memory usage.
From memory you can go into Firefox > Help > Troubleshooting and run browser in safe mode.
I use System Tools > System Monitor to keep an eye on memory usage (quite heavy if there are many tabs open).

---


---
title: "Help! Plenty of System Resources but SO SLOW!"
date: 2007-09-09
forum: General Help
---

### Post by muertetg on 2007-09-09
I'm relatively new to Linux but have learned my way around enough to make good use of the system. I have 2 gigs of RAM and a 2.5ghz pentium 4.... the only thing inadequate on this machine is the graphics card which is a Radeon 7000. Things run somewhat smoothly when I first boot, but slowly degrade. Application startup is slow and eventually I need to reboot. I'm a web developer so i usually have the following programs running thunderbird, eclipse, firefox and gaim. I know the first 3 can use a hefty amount of system resources but it should be nowhere NEAR two gigs. Occasionally I see the swap being used which (if I understand correctly) shouldn't be used unless I'm pushing the 2gig barrier. PLEASE HELP!

Right now my system is starting to bog down slowly. Here is what top tells me:

top - 22:59:42 up  8:55,  2 users,  load average: 0.46, 0.35, 0.46
Tasks: 118 total,   2 running, 115 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.8%us,  0.7%sy,  0.0%ni, 97.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   2076136k total,  1462244k used,   613892k free,    81812k buffers
Swap:  2265124k total,        0k used,  2265124k free,   964440k cached

I currently have only thunderbird, firefox and a terminal running. There is no WAY I should be using that much memory. I can't see anything specific that is taking that much.

I'm really getting annoyed and don't know where to look to fix the problem!! PLEASE HELP!!

---

### Post by swisscow on 2007-09-09
No specific solutions spring to mind but you could investigate the 2 users and the 1 zombie task showing in your top message

---

### Post by Sef on 2007-09-09
Zombie is likely one of two things:

1) You have been [hacked]("http://en.wikipedia.org/wiki/Zombie_computer").

2) Something is not [shutting off]("http://en.wikipedia.org/wiki/Zombie_process").

Since it says zombie, it likely is number 2.

---


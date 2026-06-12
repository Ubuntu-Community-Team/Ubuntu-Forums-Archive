---
title: "Chromium and Blender 3D choke system"
date: 2017-11-09
forum: General Help
---

### Post by sprinterdriver on 2017-11-09
Hi.

**Computer**
Dell Latitude D620 laptop with 3 GB ram.

**Problem**
When using Chromium for some length of time - depending of use and how many tabs is open simultaneously - the program almost all of a sudden stop responding. Things like buttons, all buttons regardless of what program is active takes forever to responds from mouse clicks.
 When this happens, I figured from top command that Chromium uses 100% CPU on both cores. I figured that swap is not an issue here (*cat /proc/swaps* command repport that 0 used swap) and also there is no sign of excessive hdd activity.

Have a similar problem with Blender 3D - but haven't investigated further (can't say for sure that CPU load is an issue here) except that the program respond slower and slower (I was following the tutorial of [making a cup - part 1]("https://www.youtube.com/watch?v=y__uzGKmxt8"), so the number of items shouldn't be enough to choke the computer).

In addition - after terminating Chromium or Blender, the computer still almost do not respond (takes forever just to open Terminal) so I didn't see any options but rebooting as soon I got Terminal running.

When I just had install Chromium browser, I'm pretty sure that this was not an issue at all. So this is a problem that have become bigger over time. In the beginning, just after the install of Xubuntu 16.04, I could open a substantially number of tabs in Chromium and it worked fine.

**Attempt to solve - not working**
So I figured I haven't yet touched swappiness. I did change swappiness to 10, but after a reboot, I couldn't see any different in behaviour.

I'm aware this is an semi-old computer released in '07 or so, But with 3 GB RAM I don't expect that Chromium should cripple it on normal use.

I want to try to try to figure out if there is some settings that makes this unfortune happens to this computer. What should I look for next?

Thanks in advance for help.

---

### Post by sprinterdriver on 2017-11-10
Have a idea about this. Back in the windows xp time, I remember that the  computer was prone to over-heating. What happens then was simply a  forced reboot of the computer.
I'm thinking this because when I read  back on first post - it's just not supposed to be possible to have that  kind of problem and that being the OS fault and neither a RAM issue.

Could it be that Ubuntu OS handles increasing CPU temp in a different matter?

In  that sense: Is it possible to set up the system somehow so that I get  an alarm sounding if cpu temp increases beyond a given temperature?

---


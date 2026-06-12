---
title: "Hangs on boot at Starting Hotplug Subsystem..."
date: 2005-08-10
forum: General Help
---

### Post by xerxesdaphat on 2005-08-10
Hi. A while ago, I downloaded Ubuntu 5.04. Very, very happy! Stable, all my hardware supported, simple to use. Anyway I've been using it about two months now, and suddenly it will not boot anymore. On boot, it just freezes at the line "Starting Hotplug Subsystem...". Now, around the forums I've seen plenty of posts saying that they've just installed linux and this problem happens - but I've already been running Ubuntu for two months with no problems, I have changed no hardware or anything. I am at a complete loss - and stressed as I have a project due in a week that I need to compile under linux!

I have (after backing up my stuff) reformatted and reinstalled Ubuntu yet same problem. After googling my ass off I have found some people saying that when hotplug hangs on boot like this a module has died, and therefore linux will not load the next module and continue booting. He vaguely described a process where I press Alt-SysReq-e to kill all the processes at runlevel 2, and then it should continue booting or something. Nothing happens when I press these keys. In fact, typing anything does not show up on the screen like normal when booting (and no, I'm not using a usb keyboard). Somebody else said that to see the module which has died, I should type in dmesg to see logs of the boot, then put the broken module in /etc/hotplug/blacklist.d. However, how am I supposed to type dmesg and blacklist modules if my computer will not boot? Anybody have any ideas? Please....?

---


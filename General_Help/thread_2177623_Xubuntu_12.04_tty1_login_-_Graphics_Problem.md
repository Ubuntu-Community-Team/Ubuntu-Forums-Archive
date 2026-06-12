---
title: "Xubuntu 12.04 tty1 login - Graphics Problem?"
date: 2013-09-29
forum: General Help
---

### Post by vincentvega2 on 2013-09-29
Problem: Xubuntu 12.04 boots into tty1 for about 30 seconds before automatically logging in. I think it is a graphics issue but I dont know how to resolve it. 

Info:  I just installed Xubuntu 12.04 to an old dell 4500 it and immediately updated it. I configured it for automatic login. Upon first reboot my monitor displayed "input not supported" and seemed to take a long time getting to the desktop about 30 seconds. I changed ```
/etc/default/grub and removed the # in front of GRUB_TERMINAL=console. 
Then sudo update-grub 
```That seemed to resolve the input problem by disabling a graphical start. 

I finally see the grub menu and select Xubuntu. Now I am presented with a tty1 login prompt. Since I setup automatic login I thought it was strange. It will accept my login and load a terminal line. Then after about 30 seconds shows the desktop. 

Some posts claim that CTRL+ALT+F7 resolves the issue. But it just removes the prompt and replaces it with a blinking cursor. But still have to wait 30 seconds to load. And its not doing anything during that time. (no hdd activity)

System:
graphics: ATI Rage128 Pro Ultra AGP vga controller (no proprietary drivers listed in "Additional Drivers")
intel pentium 4 (1.8 ghz)
kernel: 3.2.0-54

from the following posts there seems no solution to this. its either related to nvidia drivers or people just reinstall. I dont think reinstalling will work, unless maybe I dont update. While not fatal, it is a problem and would like to see if it can be resolved. 


Other posts with same problem. No resolution. 
[http://ubuntuforums.org/showthread.php?t=1646693&page=4](http://ubuntuforums.org/showthread.php?t=1646693&page=4)
[http://ubuntuforums.org/showthread.php?t=2066380](http://ubuntuforums.org/showthread.php?t=2066380)
[http://askubuntu.com/questions/186350/on-boot-black-screen-says-ubuntu-12-04-1-lts-ubuntu-name-tty1-and-asks-for](http://askubuntu.com/questions/186350/on-boot-black-screen-says-ubuntu-12-04-1-lts-ubuntu-name-tty1-and-asks-for)

---


---
title: "[SOLVED] automatically switch between xorg configurations?"
date: 2008-01-29
forum: General Help
---

### Post by Xavier Oddmon on 2008-01-29
First of all, i wasn't sure what category this would fit in, so I put it in gerneral help. I have an external hard drive, which I run Gusty Gibbon off of, and it runs quite smoothly. I use it at school, as opposed to the windows XP installed on each computer. There are two different computer labs, and this is where the problem arises. The tech department has computers with invidia cards. I'm not sure which ones, but I can check if need be. The ones in the library have integrated graphics. When I switch from two locations, it is unable to draw to the screen, so I have to hit ctrl-shift-f1, and replace my xorg.conf file with another one. I have two xorg.conf files, xorg.conf.CAD, and xorg.conf.library, and sometimes have to run dpkg-reconfigure xserver-xorg. Is there any way to switch between these automatically, based on what cards are present?

---

### Post by heindsight on 2008-01-29
have a look at this thread: [http://ubuntuforums.org/showthread.php?t=669165](http://ubuntuforums.org/showthread.php?t=669165)

---

### Post by Xavier Oddmon on 2008-02-01
Thanks! I checked it out, and as far as I can tell, it works. I'm in the library now, and i'll check it out when I get to the tech lab. It's wonderfully simple though, I see no reason for this to fail.

---


---
title: "mythtv touchscreen"
date: 2007-11-11
forum: General Help
---

### Post by egoldtech on 2007-11-11
A few weeks ago I started with the project, install mythtv on ubuntu,
I bougth a Hauppauge 500 card, and also
I got a used 15" touchscreen on ebay .
Make the touchscreen to works, via USB wasnt easy .
First I found touchscreen chip is a TSHARC something,
drivers I found on a CD were only for win, and Linux with X11RC6 , idint have idea why ubuntu didnt have this folders, so I create them, copy the driver, modifies xorg,conf, nothing worked,
but if  i cat  /dev/input/event7   (event7 says on system hardware info)
I saw streaming of characters. 
Itsharc drivers for X11 UBUNTU
[http://www.hampshirecompany.com/software/LinuxDriverUserManual_3.0.4_071001.pdf](http://www.hampshirecompany.com/software/LinuxDriverUserManual_3.0.4_071001.pdf)

[http://www.hampshirecompany.com/download/drivers.php](http://www.hampshirecompany.com/download/drivers.php)
easy to install, and starts working.

problems :
1-  to start the touchscreen daemon I have to use  :> boot.tsharc start
HOW I CAN MAKE IT START by DEFAULT on any session ????

2- MYTHTV is a litle buggie using MOUSE or TOUCHSCREEN,  there many commands and navigation buttons that do not work and I have to use the keyboard. (is my mythtv installation, or is a common problem ???)

3- If I activate "SPECIAL EFECTS" on the desktop, to have nicer windows, Cube  workspaces, etc,  I CANNOT PLAY VIDEOS, , where is the problem here? how can i start debugging?

bye eze

---


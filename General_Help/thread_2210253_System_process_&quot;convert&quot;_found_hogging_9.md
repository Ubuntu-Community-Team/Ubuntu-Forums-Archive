---
title: "System process &quot;convert&quot; found hogging 97% RAM"
date: 2014-03-09
forum: General Help
---

### Post by joshua-mounce on 2014-03-09
[COLOR=#000000][FONT=Verdana]Ubuntu Unity 12.04 64bit[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Kernel Linux 3.8.0-36-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]GNOME 3.4.2[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Memory: 1.7G[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Processor: Intel® Pentium(R) CPU P6200 @ 2.13GHz × 2 [/FONT][/COLOR]



[COLOR=#000000][FONT=Verdana]Suddenly, my system was running incredibly slow. utilizing 97% of my RAM on a constant basis with nothing active running. Poking around I found the majority of the resources were going to a process called "convert". After killing the process, I'm running smoothly at only 43% with several programs going running. Killing the processes has had no other visible effect on my system, and it only runs smoother now. Though it takes a few minutes to get there because reboots bring this right back up again. I ca[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I don't know what this process is, and it doesn't sound familiar for anything I've installed. Google has not provided any answers as to what this process is. Have I somehow stumbled upon a malware of some sort, or can someone provide me with what this process is supposed to do and why it's eating every bit of my resources? Perhaps how to kill it for good, or reset it to a normal level?[/FONT][/COLOR]

---

### Post by Vaphell on 2014-03-09
plain *convert*? afaik program with that name is a part of the *imagemagick* package and is used to transform images.

when you run ps -ux do you see its full path by any chance?

---

### Post by joshua-mounce on 2014-03-09
[COLOR=#000000][FONT=Verdana]As suggested on linuxquestions.org by user evo2, I removed Imagemagick (convert is associated with imagemagick, a file converter I hadn't installed) and the issue hasn't returned. Found out how it got onto my computer too. I had installed a program called Variety, desktop background changer. This was forcefully uninstalled during removal of imagemagick, thus they must have been bundled together. To be honest, variety had been slowing down my resources already, so I'm not surprised it was the source of the problem. Thanks for your help evo2 and linuxquestions.org!

[/FONT][/COLOR]http://www.linuxquestions.org/questions/linux-security-4/system-process-convert-found-hogging-97-ram-4175497632/

---


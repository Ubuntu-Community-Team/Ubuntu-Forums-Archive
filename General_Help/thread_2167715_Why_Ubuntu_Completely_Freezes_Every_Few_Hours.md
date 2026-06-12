---
title: "Why Ubuntu Completely Freezes Every Few Hours?"
date: 2013-08-14
forum: General Help
---

### Post by K3NrcEP on 2013-08-14
I have recently switched to ubuntu desktop LTS on my laptop which I use to host minecraft servers. It all works fine until at a random point, usually after a few hours everything freezes, it becomes completely unresponsive and not even the caps lock light works. Does anyone have a solution or at least a possible explanation?

---

### Post by VMC on 2013-08-14
Take a look at the log files, "/var/log/syslog" , "/var/log/dmesg" and "/var/log/kern.log".
Those log may not mean much to you, but see if any errors appear.

What Ubuntu are you using and what hardware?

---

### Post by K3NrcEP on 2013-08-15
I have a dell inspiron 1525 and am using the latest LTS I think 12.04. I looked briefly into the log files and will do so later again but it was over 4400 lines long :-O

---

### Post by VMC on 2013-08-15
It could be any number of things. This is your graphics:
[B]Graphics Processor: integrated Intel GMA X3100 graphics (Previously changed to 965 Express
[/B]The next time it freezes, see if you can pull up a virtual terminal - Ctrl+Alt+F1
If you can , login and type 'top' and see what process is hogging the system.

---

### Post by K3NrcEP on 2013-08-16
It almost froze and I managed to look and it seems the process largest was java however it wasn't any more than it is normally. Do you think java could cause it to freeze and crash?
This is the only thing that I could find in syslog at the time:
[COLOR=#333333][FONT=lucida grande]Aug 16 18:22:58 ubuntu acpid: client 1077[/FONT][/COLOR][/"][0:0]]("http://[0:0)[COLOR=#333333][FONT=lucida grande] has disconnectedAug 16 18:22:59 ubuntu acpid: client connected from 1077[/FONT][/COLOR][/"][0:0]]("http://[0:0)[COLOR=#333333][FONT=lucida grande]Aug 16 18:22:59 ubuntu acpid: 1 client rule loadedAug 16 18:24:31 ubuntu acpid: client 1077[/FONT][/COLOR][/"][0:0]]("http://[0:0)[COLOR=#333333][FONT=lucida grande] has disconnectedAug 16 18:24:31 ubuntu acpid: client connected from 1077[/FONT][/COLOR][/"][0:0]]("http://[0:0)[COLOR=#333333][FONT=lucida grande]Aug 16 18:24:31 ubuntu acpid: 1 client rule loaded

Not sure about dmesg as it has no time stamps.[/FONT][/COLOR]

---

### Post by K3NrcEP on 2013-08-16
Actually looking over the server log it seems that it is happening from the java server crashing, I'll keep an eye on it and say if that's what's causing it for definate.

---


---
title: "Unable to use launcher to start Amok Exifsorter java application"
date: 2008-04-03
forum: General Help
---

### Post by v.vanhala on 2008-04-03
Hi.

I'm using Amok to transfer pictures from my camera to my harddrive. The problem is i can only launch it from the terminal or by clicking it in nautilus. It is a java application that uses sh script to launch it. 
> #/bin/sh
java -Djava.library.path=. -jar Exifsorter.jar
Naturally i just tried to make a launcher for this with "/home/valtteri/Documents/Exifsorter_2.5.1/Exifsorter.sh" but nothing happened. I figured it would need to cd it to the location. Thus i tried this.
> #!/bin/sh
cd /home/valtteri/Documents/Exifsorter_2.5.1
java -Djava.library.path=. -jar Exifsorter.jar
This works when run from within the directory just like before but if i move it to the desktop it won't work anymore. This beats me cause if i copy these commands to the terminal it works just fine. Why won't they work in a script like this? 

If i run the new file from the desktop with "sh Exifsorter.sh" it says:
> cd: 2: can't cd to /home/valtteri/Documents/Exifsorter_2.5.1/
Unable to access jarfile Exifsorter.jar

Why can't it cd to the directory? It does that just fine when i paste that line to terminal. What needs to be changed?

---


---
title: "wtf where r my files??"
date: 2008-01-16
forum: General Help
---

### Post by giok13 on 2008-01-16
k well ive ubuntu for a while but now i installed compiz, and it worked for like a week or two but know everything disapeared. my files on my desktop r gone. i cant open my computer folder, or home folder or any folder at all. can anyone help?

---

### Post by bodhi.zazen on 2008-01-16
hard to tell from your descritpion.

if you create a new user, is the new user working ?

did you change the name or permission of $HOME ?

---

### Post by geirha on 2008-01-16
I've encountered something similar to this a few times, that is, no icons on the desktop. The thing is, nautilus (which is the file browser) is the program responsible for drawing the icons on the desktop, but if it fails to do this for whatever reason, you will get an empty desktop. A quick fix for this is to kill the running nautilus, which will be detected by gnome, and a new one will be started. So try this in a terminal: ```
killall nautilus
```

Logging out and logging in again probably works too.

Your explanation is a bit vague though, so it might be a different problem.

---

### Post by giok13 on 2008-01-16
k wen i open my home folder i get this pop-up saying

 Could not open location 'file:///home/user'
There is no default action associated with this location.

ill try creating a new user now. but im not sure if i changed the premision or not cause i did some stuff trying to get plugins into my compiz. but also wen i go into my terminal and change the disk to desktop it works. i put cd ~/Desktop and it changed it to it and thn i remembered one of the folders tht was on my desktop and i typed cd ~/Desktop/mac and it changed the folder thr too. so it looks as if ubuntu itself cant open or read the fil, and folders or something.

and yes i do remember uninstalling and thn installing nautalus because i wanted to have plugins on compiz i followed this guide

[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

and also wen i was following the guide, i had to remove nautalus and reinstall it and wen i was reinstalling it something wen wrong and it gave me an error but thn i tryed it again and it worked, well i think it worked so it prbly is because of nautalus but i tried to kill nattalus but i got this nautilus: no process killed. is thr a way to completly uninstall and thn install nautalus all over again?


solved by sudo apt-get install nautalis

---

### Post by SunnyRabbiera on 2008-01-16
yeh i had hiccups like this too, hopefully a re login will help

---

### Post by geirha on 2008-01-16
Try ```
sudo aptitude reinstall nautilus
sudo dpkg --configure nautilus
``` in a terminal

---

### Post by gumpontheweb on 2008-01-28
I have the same exact problem!!!!
I don't have aptitude  installed so when I put the line in that's what it tells me.
when I went to synaptics to get aptitude it showed lots of things that had to be removed to get it so I didn't. What else is an alternative?

---


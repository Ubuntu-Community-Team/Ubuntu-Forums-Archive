---
title: "using acetoneiso2 and vmware"
date: 2007-07-04
forum: General Help
---

### Post by spartan777 on 2007-07-04
i'm trying to figure out how to mount an image ( a windows one ) with acetoneiso2 pro that is recognizable by my virtual machine on vmware. for whatever reason, acetoneiso mounts iso's under /home/myname/virtual-drives/* (* is a # 1-8). of course, my vm won't recognize that iso. also, I can't seem to change the directory to where i can mount iso's in acetoneiso. how can i get my vm to see my .iso?

---

### Post by spartan777 on 2007-07-04
solved! right after i posted that, i was looking around in vmware, and apparently i can create a new "CD/DVD DRIVE" just using the .iso image. all I had to do was point vmware to the .iso file, and it made it its own drive, and everything works. too bad about acetoneiso2, version 1 was much better. the new one is kinda weird and less intuitive.

---

### Post by bulletxt on 2007-07-11
well maybe you should completely check out the program. AcetoneISO2 introduced automatic mount to make it easier and way faster. but they didn't forget about users that needed to mount in a specific directory.
first of all, open AcetoneISO2, then click on the green + button. now go under "utilities" and you will find "Generic Mount". as the word says it will let you mount an image in a generic folder that the user wants.

they didn't forget about power users ;)

---

### Post by spartan777 on 2007-07-19
I can't click the green button. the program works in all other ways but this. I'm in gnome as always, but I don't think that should affect it.

---

### Post by bulletxt on 2007-07-20
yep, I have just found the same bug. it worked with qt4 4.2 but now i updated to 4.3 and it's not working anymore, and the display has changed colour. what a mess! I hope the team is aware of this issue with the new qt 4.3, I'll send them an email so they can fix it :)

I've also just found out that there is a port for gnome users. it seems it is meant for people who don't want to install kde libraries :D  more info :
[http://www.acetoneteam.org/acetoneiso-gnome.html](http://www.acetoneteam.org/acetoneiso-gnome.html)

however I'm sure the green button will still give problems :P

---


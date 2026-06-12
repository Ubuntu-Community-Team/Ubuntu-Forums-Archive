---
title: "Partimage &quot;GUI&quot;"
date: 2007-01-16
forum: General Help
---

### Post by DapperMe17 on 2007-01-16
Wondering if there is an easy way to deploy the GUI for Partimage in Ubuntu?


Thanks

---

### Post by codejunkie on 2007-01-16
> **DapperMe17 said:**
> Wondering if there is an easy way to deploy the GUI for Partimage in Ubuntu?


Thanks
what do you mean by the gui for partimage? if your talking about the partitioning tool on the ubuntu livecd you can add it to your install by running```
sudo aptitude install gparted
```in a terminal.

---

### Post by DapperMe17 on 2007-01-16
No,

I want to make Ubuntu backups, with Partimage. I want to use the GUI, not from command line.

Any way to do it?

---

### Post by Sef on 2007-01-16
Get [Partimage]("http://partimage.org/Main_Page").
Once you download and burn it, you can make the back ups with no problem.

---

### Post by drr422 on 2007-01-16
Although Partimage is a Command line tool, all you have to do is type partimage and it will take up the terminal session with a GUI'ish iterface. Don't worry about it not being a GUI, the only command you'll need to know is partimage. After that, you can select the partition you want to image, then the location you want to store it, and after that you can select the compression you want.  Over all its very simple.

EDIT:  I havn't heard of a GUI for partimage though, although there are lots of things that i havn't heard about :-P

---

### Post by ardchoille42 on 2007-01-16
I use Partimage a lot and it has a GUI. Just type partimage at the command line and the GUI will run. Here are screenshots of Partimage in action:

[http://www.partimage.org/Screenshots](http://www.partimage.org/Screenshots)

It may not look like a GTK2 GUI, but it is point and click.. no commands needed.

---


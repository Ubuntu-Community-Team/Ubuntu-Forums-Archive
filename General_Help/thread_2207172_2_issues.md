---
title: "2 issues"
date: 2014-02-22
forum: General Help
---

### Post by jrmchess on 2014-02-22
Hi guys,

I have 12.04 and using the kde desktop. I am facing 2 issues:

1. There is some cracking sound coming from my speakers whenever I connect a headphone (this problem started only after switching to kde). I tried the suggestion here [http://askubuntu.com/questions/276769/ubuntu-12-10-crackling-and-popping-sound](http://askubuntu.com/questions/276769/ubuntu-12-10-crackling-and-popping-sound) but it doesn't work.

2. How do I set the shortcuts for terminal as ctrl-alt-T and ctrl-alt-del for the task manager?

Thanks

---

### Post by SeijiSensei on 2014-02-22
For (2), all the shortcuts are managed from System Settings > Shortcuts and Gestures.

---

### Post by jrmchess on 2014-02-22
> **SeijiSensei said:**
> For (2), all the shortcuts are managed from System Settings > Shortcuts and Gestures.

yes I went there but can't figure out how to set a shortcut for the terminal as I don't know what command to use in the custom shortcut field for "Konsole".

---

### Post by ajgreeny on 2014-02-22
Try simply **konsole**

---

### Post by jrmchess on 2014-02-22
> **ajgreeny said:**
> Try simply **konsole**

thanks it worked. how about ctrl-alt-del for the task manager?

---

### Post by SeijiSensei on 2014-02-22
What task manager?  There isn't a program that I know of like the Windows equivalent.  That doesn't mean there isn't one, though, since I manage balky tasks from the command prompt using "top" or "kill/killall".  Top is the closest thing I can think of to a task manager, but it basically only allows you to kill jobs or to "[renice]("http://linux.die.net/man/8/renice")" them, which affects their scheduling priority.

One way to find out the name of a program is by right-clicking on the K menu button and choosing "Edit Applications."  Then you can select an application from the menu list in the left pane and see the corresponding application name in the right pane.

---

### Post by jrmchess on 2014-02-22
I think I resolved my first problem from here [http://askubuntu.com/questions/175602/periodic-clicking-sound-from-pc-speaker](http://askubuntu.com/questions/175602/periodic-clicking-sound-from-pc-speaker)

> It seems that the problem resides within the Intel High Definition  Audio drivers, and it has been around for quite some time now.
  To solve the problem temporarily, but immediately, issue the following command:
  echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save
  Try the previous command to be sure you are suffering this problem.  If this works for you, then you can solve it permanently by adding the  following line above "exit 0" in "/etc/rc.local".
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save


---

### Post by ajgreeny on 2014-02-23
There is a GUI application similar to Task Manager but it depends on which DE you use and as I don't know KDE any more I can't tell you what it may be called, though a quick search suggests it is Task-manager.

Have a good look through the menu and you might find something.

---

### Post by SeijiSensei on 2014-02-23
There's no task manager in my copy of Kubuntu 14.04.  Typing "ta" at the prompt and hitting tab brings up nothing of relevance:
tabs        tac         tail        tailf       tap2deb     tap2rpm     tapconvert  tar         tarcat      taskset

Using capital-T doesn't help.

---

### Post by oldos2er on 2014-02-23
Doesn't Ctrl-Esc bring up a process manager or viewer in KDE?

---

### Post by timgood on 2014-02-23
System Monitor is your friend.

---

### Post by jrmchess on 2014-02-23
> **ajgreeny said:**
> There is a GUI application similar to Task Manager but it depends on which DE you use and as I don't know KDE any more I can't tell you what it may be called, though a quick search suggests it is Task-manager.

Have a good look through the menu and you might find something.

I found it. It's called ksysguard

---

### Post by SeijiSensei on 2014-02-24
> **oldos2er said:**
> Doesn't Ctrl-Esc bring up a process manager or viewer in KDE?

So it does.  It's pretty much a graphical version of top, except that right-clicking on a task brings up some additional informational choices.

---


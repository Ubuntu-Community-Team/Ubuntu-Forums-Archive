---
title: "Computer appears to go into power save but wont come back out"
date: 2007-06-06
forum: General Help
---

### Post by kc0eks on 2007-06-06
Hello all,

I am not even sure how to describe this completely so here goes.
Within the last few days (I would say 3 days) I have now on several occasions come back to my computer after a few hours to find the monitors in power save mode. This is all fine and well except that moving the mouse doesnt bring it back. 

Ctrl-alt-backspace does nothing
ctrl-alt-del does nothing
switching to console modes does nothing (ctrl-alt-f1,2,3 etc)

The only thing I can do is a hard reset. 

I have always had my monitor set to turn off after a certain amount of time, but now it started doing this all the sudden. I dont think I changed anything, but I have applied recent updates. I have looked through logs but I didnt see anything that jumped out at me as the cause (but I may not know what to look for either)

I would love some help on this one, as rebooting every time I come back is becoming old :)

Thanks all!

---

### Post by DagMan on 2007-06-06
First, in power manager do you have your computer set, assuming the option is there, to suspend or standby after a set period of time, if so then perhaps it's not the screenblanking but the suspend or hibernate that's doing it.

If it isn't that, and the following creates the problem:
```
sudo /etc/acpi/screenblank.sh
```
then you can either make that script unexecutable or just edit it so that the first line after #/bin/bash says exit
This would make it so your screen doesn't blank.

Look at 
```
man xset
```
for some command line options to blank the screen.  I don't know how to use it that well myself but there's some good info if you google it on how to use the command effectively and you could make script to do it.
Another thing to consider would be uninstalling gnome-screensaver and installing xscreensaver to let xscreensaver handle your screen blanking after disabling it in power manager entirely. xscreensaver-demo is the command to run the xscreensaver options screen.  You'de have to add xscreensaver to your startup too like this:
```
xscreensaver -no-splash &
```

---


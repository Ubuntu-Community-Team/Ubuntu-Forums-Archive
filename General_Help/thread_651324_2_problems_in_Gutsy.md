---
title: "2 problems in Gutsy"
date: 2007-12-27
forum: General Help
---

### Post by zenwalker on 2007-12-27
Hello Friends,

Well i am experiencing 2 problems in Gnome of Gutsy. One at boot up and second at shutdown/logoff/restart.

1) After i give out username and password at login page, i get a orange screen with out any small window appearing which shows the loading of stuffs before Desktop comes up. This was occuring in Fiesty.. Is it a bug or should i do some settings change??

2) When i press Quit button either in Taskbar or under System menu. The system will take around more than 2 mins to show up the closing screen or perhaps Quit screen which has Shutdown, Restart, logoff, etc buttons on it to be selected. Again is it a bug or not? And in the mean time (b/w 2 mins or so duration) my desktop is kind of locked state. I cant do any thing. Gotta wait till that screen comes up. This happens always. Disabled ACPI, but no use.. So whats work around?

Thanks,
Zen :)

---

### Post by zenwalker on 2007-12-27
Any body please?

---

### Post by nick_h on 2007-12-30
1. It sounds like your Gnome splash screen is missing.  There is another thread [here](http://ubuntuforums.org/showthread.php?t=459098) and a bug reported [Bug #146893](https://bugs.launchpad.net/ubuntu/+bug/146893).

2. The logout screen should appear quickly.  For a workaround, shutdown from a terminal using:
```
sudo shutdown -h now
```

---


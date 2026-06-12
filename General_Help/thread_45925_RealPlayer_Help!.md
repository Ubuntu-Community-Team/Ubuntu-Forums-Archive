---
title: "RealPlayer Help!"
date: 2005-07-02
forum: General Help
---

### Post by deltablaze on 2005-07-02
Hi! Well I've been using Hoary Ubuntu for two days, and I am impressed. So impressed I deleted my windows installation. Ok, on to the point. I did sudo apt-get install realplayer. RealPlayer installed nicely and worked, but then I had a problem with my volume, so I restarted so I could watch my video on realplayer. Then what happened is I opened realplayer and nothing happened. I tried to reinstall it by doing sudo apt-get  remove realplayer. It removed and I installed it again like the first time. Still the same problem. Help please :)

---

### Post by Xian on 2005-07-02
[QUOTE=deltablaze] Then what happened is I opened realplayer and nothing happened. I tried to reinstall it by doing sudo apt-get  remove realplayer. It removed and I installed it again like the first time.[/QUOTE]
It sounds suspiciously like a sound conflict on your system.

Test this by first making sure that you don't have any instances of realplay running in the background. If you don't know how to do this, then just reboot. When you've satisfied this condition open a terminal and issue the command below. Then try and run RealPlayer again. If you can get the application to run at that time you will likely want to read [THIS](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple) thread.

```
$ killall esd
```

---

### Post by deltablaze on 2005-07-02
[QUOTE=Xian]It sounds suspiciously like a sound conflict on your system.

Test this by first making sure that you don't have any instances of realplay running in the background. If you don't know how to do this, then just reboot. When you've satisfied this condition open a terminal and issue the command below. Then try and run RealPlayer again. If you can get the application to run at that time you will likely want to read [THIS](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple) thread.

```
$ killall esd
```[/QUOTE]
 Aha, cheers dude. Thanks youve solved my problem :) 10/10

---


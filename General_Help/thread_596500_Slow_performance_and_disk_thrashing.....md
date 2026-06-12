---
title: "Slow performance and disk thrashing...."
date: 2007-10-29
forum: General Help
---

### Post by road_rage on 2007-10-29
I am a suber n00b, but just built new fast system and still working on getting everything setup. I installed Amarok using the default SQLite db and all was good. Now when I launch the app (Amarok) it is very slow to launch and once launched it is thrashing the disk over and over and takes about a minute everytime I select an action like pause, next track etc. 

I read the threads on db's and guess that could be related, but I only have a small number of songs/artists and can't believe the db is that pathetic  ? Is this more related to the KDE app vs. the Gnome app thing ? Is there anything you could recommend I try before aborting Amarok ?

I have looked at a number of musc apps and they all seem to be somewhat close but not quite all the features that this had to offer. Any suggestions ?

--RR

---

### Post by Crafty Kisses on 2007-10-29
> **road_rage said:**
> I am a suber n00b, but just built new fast system and still working on getting everything setup. I installed Amarok using the default SQLite db and all was good. Now when I launch the app (Amarok) it is very slow to launch and once launched it is thrashing the disk over and over and takes about a minute everytime I select an action like pause, next track etc. 

I read the threads on db's and guess that could be related, but I only have a small number of songs/artists and can't believe the db is that pathetic  ? Is this more related to the KDE app vs. the Gnome app thing ? Is there anything you could recommend I try before aborting Amarok ?

I have looked at a number of musc apps and they all seem to be somewhat close but not quite all the features that this had to offer. Any suggestions ?

--RR

You might want to check your resources, open up the Terminal and type:
```
top
```

---

### Post by road_rage on 2007-10-29
I ran the command and it looks pretty much how I figured, idle and underutilized. That is what I can't get, the system is pretty fast, it is just when I ran Amarok it starts misbehaving and thrashing and slugging. I have been going through all of the settings in the app, but nothing so far. I have also been reading up in the cafe about other players and what people are using/happy with. It seems that the majority is for Amarok whether on ubuntu or kubuntu. I just can't find anything to troubleshoot or look at to figure out the issue. It seems most people who have issues just abandon the app and move to another player. 



```
Tasks: 123 total,   1 running, 121 sleeping,   0 stopped,   1 zombie
Cpu(s):  6.5%us,  0.2%sy,  0.0%ni, 93.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2074856k total,  2020492k used,    54364k free,   369328k buffers
Swap:  3028212k total,    34804k used,  2993408k free,  1038256k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
20549 rr              15   0  285m 153m  27m S    7  7.6  14:35.99 firefox-bin        
16974 rr              15   0  227m  91m  32m S    6  4.5 540:44.19 amarokapp          

```

---


---
title: "Applets taking up lots of memory"
date: 2007-08-15
forum: General Help
---

### Post by MikeBenza on 2007-08-15
I took a closer look at top and what processes are utilizing the most memory.  I was surprised to find a number of applets are using a lot of memory:

```

  PID USER      PR  VIRT  RES  SHR %MEM    TIME+  COMMAND 
 6038 mike      15  192m  58m  21m  9.3   0:47.12 firefox-bin
 6071 mike      15 47888  20m  13m  3.3   0:01.74 gedit
 4645 root      15  218m  18m 7812  2.9   0:33.61 Xorg           
 5793 mike      15 46340  17m  13m  2.8   0:03.20 gnome-panel    
 5795 mike      15 79116  17m  12m  2.8   0:01.73 nautilus       
 5978 mike      15 49516  14m 9240  2.3   0:05.14 gnome-terminal 
 5931 mike      15 37528  12m 8988  1.9   0:00.62 **mixer_applet2**
 5812 mike      15 35672  11m 8480  1.8   0:00.58 **update-notifier**
 5035 mike      16 21452  10m 8144  1.7   0:00.79 x-session-manag
 4603 root      21 13612  10m 1168  1.7   0:00.00 perl           
 5810 mike      15 45164  10m 8564  1.7   0:00.45 **mail-notificati**
 5822 mike      15 34528  10m 8740  1.6   0:00.35 **nm-applet**
 5814 mike      16 67980  10m 8672  1.6   0:00.30 evolution-alarm
 5289 mike      15 29596  10m 7992  1.6   0:00.88 gnome-settings-
 5877 mike      16 27944 9608 8000  1.5   0:00.29 evolution-excha
 5933 mike      15 35004 9568 7608  1.5   0:00.27 **gnome-netstatus**
 5874 mike      15 67152 9268 7468  1.4   0:00.27 **trashapplet**
 5788 mike      15 15560 8796 6752  1.4   0:02.54 metacity       
 5829 mike      15 34692 7740 5912  1.2   0:00.15 gnome-power-man
 5856 mike      15 65440 6544 5220  1.0   0:00.19 evolution-data-
...

```These applets are using at least 10% of my memory, which is a lot more than I think is reasonable.  I saw [this thread]("http://ubuntuforums.org/showthread.php?t=183061") already, but it didn't have any solution, and my issue isn't as severe, so I don't think it's the same problem.  This problem was happening on Dapper last night, and now it's happening on Edgy now (I upgraded last night, hoping that might fix the problem).  I'll upgrade to Feisty later tonight, but for some reason, I don't think the problem will be fixed.

- Mike

---


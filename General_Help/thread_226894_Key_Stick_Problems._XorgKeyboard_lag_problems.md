---
title: "Key Stick Problems. Xorg/Keyboard lag problems"
date: 2006-07-31
forum: General Help
---

### Post by lemix on 2006-07-31
This is a new problem for me. when typeing i hit turbulence and one of the keystrokes repeats itself about 10 times. it can be space enter or any character. It makes it hard to type one sentence without going      back and editing it. << i pressed space in that last sentence and it repeated it about six timesssssss.

with as much as you use the terminal in linux i find it very difficult to use the operating ttttthis system with ubuntu iiiiinstalled. It is close to a freash install and i have no idea what the trouble is.

> top - 20:50:47 up 10:19,  2 users,  load average: 0.40, 0.35, 0.21
Tasks: 100 total,   1 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.0% us,  0.0% sy,  0.0% ni, 96.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1035968k total,   780600k used,   255368k free,    58160k buffers
Swap:  2409708k total,        0k used,  2409708k free,   517640k cached
  
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4345 root      15   0 65284  37m  11m S  2.3  3.7  14:53.15 Xorg
 4885 dom       15   0 15320 9264 6452 S  0.7  0.9   0:10.79 metacity
17148 dom       15   0 84720  17m  11m S  0.7  1.7   0:12.69 gaim
 4525 haldaemo  16   0  2012  820  716 S  0.3  0.1   0:00.91 hald-addon-stor
 4876 dom       15   0 27328 9088 6952 S  0.3  0.9   0:01.01 gnome-settings-
20682 dom       15   0 83484  13m 8752 S  0.3  1.4   0:00.80 gnome-terminal
    1 root      16   0  1568  528  460 S  0.0  0.1   0:01.73 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  124 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  125 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  127 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0



there is nothing odd runninnnnng to me. Im looking for a quick and easy     fix.

I dont want to switch back to slackware but i will if the problem persists.
All help is appreciated.
     -lemix

---

### Post by professor_chaos on 2006-07-31
does disabling the repeat option in the Main Menu->System-> Prefs->Keyboard help any?

---

### Post by lemix on 2006-08-01
Well. Yes. I have done that but i found myself waiting for me to delete errors many minutes. The backspace doesnt repeat. If no keys but the backspace repeated then i would accidently erase most of my sentence whenever i used it.

On another note, I have noticed that it doesnt happen right away when i restart. This problem is completely visable, even if i turn keyboard repeat off when i am typing i still get keyboard lag. I am currently wandering about other forums looking for an alternative solution.

Thank you for posting. Helps very much but still not the same to be lagging with a machine with my specs. something is definetly wrong and i am eager to find a solution to this problem.

~~ If not posting for me, Post for Beans!!!~~

---

### Post by Bagnaj97 on 2006-08-01
Do you have a package called plptools installed (I think that's it)? It's for connecting to Psion PDAs but there's a bug in it that causes keyboard problems.

---

### Post by lemix on 2006-08-01
The last thing i installed had to be KDE. at least from synaptic. I am almost positive that thats not the cause of the problem.

Almost fresh installed besides Display driver install and Never Winter Nights.

I copied some files over from windows, They are probably using 100's of MB of ram just because they were born in windows. Ill make sure i kill them.

---

### Post by Bagnaj97 on 2006-08-01
there is a bug listed here [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/39315) with a few possible fixes, that's where I found out about plptools which was causing my problems.

---


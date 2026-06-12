---
title: "Help me make  ascript to terminate a programme  (and start it again)"
date: 2007-02-16
forum: General Help
---

### Post by seshomaru samma on 2007-02-16
I'm participating in a Stanford university research project that could potentially cure some cancers, alzheimers, parkinsons, etc . I'm helping by donating some of my computer RAM which together with other people's computers form some sort of super computer which analyses protein folding (more info [here ]("http://folding.stanford.edu/"))
Anyway , I've downloaded their client and it runs in the background without disturbing me . It does disturb my wife who claims it slows down the computer (she sees the CPU on the gdesklet going to 100%) . The problem is that stopping the programme involves a bit of terminal work ,which she refuses to do. Perhaps there is a better way but the only way I know to make it stop is to go 
```
ps aux | grep FAH
```
the output usually looks like this :
```
sesho    10248  0.7  7.2 105652 74568 pts/0    SN+  11:23   0:01 ./FahCore_a0.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 10242 -version 504
sesho    10249  0.0  7.2 105652 74568 pts/0    SN+  11:23   0:00 ./FahCore_a0.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 10242 -version 504
sesho    10250 77.7  7.2 105652 74568 pts/0    RN+  11:23   2:10 ./FahCore_a0.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 10242 -version 504
sesho    10251  0.0  7.2 105652 74568 pts/0    SN+  11:23   0:00 ./FahCore_a0.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 10242 -version 504
sesho    10394  0.0  0.0   2888   816 pts/1    S+   11:26   0:00 grep Fah
```
and then kill all (usually about 4) processes that come up
I wonder if anyone can help me write a script or something that I can put on the desktop and my wife could just press in order for it to stop the programme.
Thanks

---

### Post by yabbadabbadont on 2007-02-16
Try running, "killall FahCore_a0.exe", in a terminal window and see if all instances of the process quit.  If so, just create a custom launcher that runs that command when selected.

---

### Post by seshomaru samma on 2007-02-17
thanks 
it worked

---


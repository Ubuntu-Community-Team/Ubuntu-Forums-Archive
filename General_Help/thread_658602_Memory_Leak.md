---
title: "Memory Leak"
date: 2008-01-04
forum: General Help
---

### Post by mcgodx on 2008-01-04
I have a pretty bad memory leak I think.  I heard that the new nVidia drivers have a pretty bad one, so I got rid of mine, and installed the 169.04 beta drivers, as I was told that it would help to fix it.  The drivers work just fine, however it seems like the leak is still here, as bad as ever.  When I use top:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5734 mylan     15   0 1003m 798m 777m S    0 39.6   2:42.40 compiz.real        
 5400 root      16   0  357m 279m  30m R    2 13.9   8:49.68 Xorg               
 6088 mylan     15   0  188m  94m  20m S    0  4.7   8:33.13 firefox-bin  
```
Here are the biggest offenders.  When I look at free -m:
```
             total       used       free     shared    buffers     cached
Mem:          2013       1998         15          0          7        479
-/+ buffers/cache:       1511        502
Swap:          486         37        448
```
Is what I get.  Right now I have no slowdown that I can tell, but the computer has only been on like 2 hours.  Maybe a little less.

Is there a fix for this?  I have been hearing a lot of issues with compiz and memory leaks, and I just wonder why Ubuntu put it in the release if it's not that stable yet.

Anyways, any help is greatly appreciated.

---

### Post by thetimekeeper on 2008-01-05
I think I have the same problem. Been trying to solve it for a while now, very irritating after I have to restart the x session after a hour or so of work, when the leak gets bad. I've tried a variety of solutions, and just tried turning off trackerd to see if it helps.

---

### Post by mcgodx on 2008-01-05
Just a little more info I forgot to mention.
When I do the following using the Alt+F2 run command:```
metacity --replace
compiz --replace
```
My memory usage goes down substantially until it builds up again.  Just now it went down about 400MB.

---

### Post by nchase on 2008-01-09
Are you running gnome with session saver enabled?

If so, try this -- it seems to have helped me. Been running all morning with zero swap file/memory hogging problems from xorg:

[LIST][*]disable "Automatically remember running applications when logging out" in Sessions options (under preferences)
[*]delete ~/.gnome2/session (disabling the feature does not remove the current gnome session file, causing the session (and memory hogging behavior) to return on startup)
[*]:guitar:[/LIST]

---


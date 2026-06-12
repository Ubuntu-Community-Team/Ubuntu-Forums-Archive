---
title: "Cannot force kill &quot;obs studio&quot; process even as root and SIGKILL"
date: 2019-07-22
forum: General Help
---

### Post by hk1ll3r on 2019-07-22
I am amazed that I cannot kill the "obs" process on my ubuntu 18.04.2 LTS.

$ ps aux | grep obs
hossein   5319 22.1  2.6 11733624 852096 ?     R    14:00  71:02 obs
root     19838  0.0  0.0  23088  1084 pts/5    S+   19:21   0:00 grep --color=auto obs

I tried killing by process id:
$ kill -9 5319  

killing by name:
$ pkill -9 obs
$ killall -9 obs

but neither works. The process lives on and HAS THE SAME ID after. So it is not getting restarted.

$ ps aux | grep obs
hossein   5319 23.5  2.6 11733624 852096 ?     R    14:00  77:02 obs
root     19969  0.0  0.0  23088  1080 pts/5    S+   19:27   0:00 grep --color=auto obs

I tried "su"ing and tried all of the above as root. Still no luck. 

obs process is keeping a single core at 100%.

The GUI shows "obs is not responding" message continuously but it doesn't matter whether I press "Force Quit" or "Wait". 

HELP PLEASE! THIS IS ABSURD!

---

### Post by hk1ll3r on 2019-07-22
I restarted "lightdm" and that killed "obs". I noticed my webcam stayed on after the restart. It normally shuts down when I quit obs studio. So I decided to restart my laptop just in case since I had lost all my open apps already. During shutdown I go the following error: (typing from memory)

[ failed ] cannot unmount /run/user/1000

Any explanations for the whole situation?

---


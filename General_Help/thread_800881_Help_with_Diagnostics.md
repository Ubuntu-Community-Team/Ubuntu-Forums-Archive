---
title: "Help with Diagnostics"
date: 2008-05-20
forum: General Help
---

### Post by alwbsok on 2008-05-20
I've recently installed Hardy, and it's going pretty well. No major complaints just yet. There's just something that irritates me every now and again: the cpu gets maxed, the computer freezes for just a couple of seconds, and returns to normal. Instead of asking if anyone else has had the same irksome little experience, I want to know how you diagnose problems of this nature (i.e. infrequent, unexpected, difficult to pinpoint). What software do you use? Are there any bash commands that could help me log cpu usage of processes, or any errors they output without monitoring specific processes one at a time? Thanks in advance.

---

### Post by brownicb on 2008-05-20
Have you tried the top command?  This should tell you which processes are utilizing the most resources on your system.

---

### Post by jakupl on 2008-05-20
or htop. it is a tad better.

---

### Post by eldragon on 2008-05-20
i had this problem right when gutsy was out.

the culprit was the vino vnc server.

run on a terminal ps -e |grep vino
if its running, disable it. and see if your problem goes away.

---

### Post by alwbsok on 2008-05-20
I tried top and htop (thanks to those who suggested them :)). They should prove useful, but I'm more looking for a daemon that can help log these things over long periods of time. The problem occurs extremely sporadically, and I don't have the time (nor the cpu cycles) to open a terminal, enter in $top, and find the process responsible before the problem goes again.

---

### Post by bingoUV on 2008-05-20
Daemonize top. It will take some CPU cycles every 2 seconds(change the -d 2 option below if you want some other interval), but only until you diagnose your problems.
```

top -b -c -d 2 > /tmp/topResults

```

Just after you have your freeze-ups, look around the last part of the file /tmp/topResults and you might find your culprit.

---

### Post by alwbsok on 2008-05-21
Thanks! That's exactly what I wanted!

---

### Post by alwbsok on 2008-05-21
OK, I've tried it, and I was lucky enough to catch the bug before the file became too massive. Unfortunately, even though the bug went on for more than two seconds, it didn't log any usage over 10% (despite the CPU monitor showing it to be maxed out). I'm guessing whatever is taking all those cycles has a higher priority, so I might try the same process with a very low nice value.

One thing I did find out is that I have a "zombie" process: python. Would that account for anything?

---

### Post by bingoUV on 2008-05-21
In top's output, include the "wa" cpu percentage in your analysis. Your CPU monitor could be showing this as almost 100%. Which CPU monitor do you use?

---

### Post by alwbsok on 2008-05-22
wa is minimal. "id" is larger, but I'm guessing it stands for idle. I use the taskbar widget that comes with ubuntu.

I'm still yet to isolate the bug while logging. I used the command "sudo nice -n -20 top -b -c -d 2 > ~/topResults" I'll assume that it's correct and safe until anyone tells me otherwise.

---

### Post by alwbsok on 2008-05-22
OK, I've isolated the bug on nice -20, but still no show on the stats. Oh well.

---


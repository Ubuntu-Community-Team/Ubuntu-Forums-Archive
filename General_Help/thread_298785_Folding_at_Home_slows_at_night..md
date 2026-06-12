---
title: "Folding at Home slows at night."
date: 2006-11-13
forum: General Help
---

### Post by sgstarling on 2006-11-13
It's been 3 or 4 days since I installed FAH. I've been keeping an eye on the FAHlog.txt, watching it's progress.

I've noticed that during the day, when I'm busy using the computer, it's progress is relatively constant and frequent. i.e. 56%...57%....58%.59%

But when I go to bed and it's, say, at 59%, then when I wake up and check it, it's like 59%...............................

And shortly after I wake up, there will be progress, then 60%. 

Basically, FAH will progress about 30% during the day, then none or 1 during the night.  I don't have any power saving mode selected, except display goes off after 20 minutes. But that couldn't be it, could it? Anyone know what it could be?

---

### Post by organica on 2006-11-13
It knows when you sleep!!!!   

JK

Have you looked into this on Stanford's side?  Also, have you watched the CPU and processes at night?  maybe something else kicks in on your cpu and pushes the FAH process back to a lower priority?  No telling really.

---

### Post by jpkotta on 2006-11-16
I'll bet it's your screensaver.

You can see what's taking up all the CPU time with something like this:

```
while true ; do date >> ~/CPU.log ; ps -e -o %cpu,user,cmd | sort -nr | grep -v '^%' | head >> ~/CPU.log ; echo >> ~/CPU.log ; sleep 300 ; done
```

This will show the top 10 processes by cpu usage, and write them to the file CPU.log every 5 minutes.  CTRL-C to cancel it.  Let it run overnight and you'll see who's hogging the CPU.

---


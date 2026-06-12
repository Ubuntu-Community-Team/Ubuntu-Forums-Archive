---
title: "[SOLVED] Dual Core CPU acting strangely"
date: 2007-12-13
forum: General Help
---

### Post by PsyWolf on 2007-12-13
I noticed recently that whenever I try to do something at all CPU intensive on my computer, the percent of the cpu power in my little CPU monitor on my task bar seemed to cap at 50% and stay there.  My first guess was that one of my cores wasn't being used and the other one was being maxed out my something, but then I opened my System Monitor and found that both CPUs were working but they were staying relatively inversely proportional (the closer core one got to 100% the closer core two got to 0% and visa versa).


here is a screenshot that describes it better than I can in words.  This is me trying to play warcraft III with cedega.  Now My computer is perfectly capable of handling this, but recently stuff has started to get choppy during gameplay and that is why I started looking into this.
[IMG]http://i4.photobucket.com/albums/y149/RidgeWolf/CPUs.png[/IMG] 

when i did some further research, I saw this happening any time I put any significant load on my CPU.

I don't know a lot about dual core CPUs.  Maybe this is normal?  It just didn't seem right to me so I thought I would ask on the forums to see if this is supposed to look like this.  If it isn't how can I go about fixing it.  Is there something I must do to optimize Ubuntu for my processor.  It is a fairly standard Pentium D.  Nothing special.

---

### Post by PsyWolf on 2007-12-14
come on someone has to know if this is normal or not

---

### Post by flamelab on 2007-12-14
No worry . That happens if a program is not multi core optimised . If it is you may use more than 50 % of your CPU , or it will use only one of the two possible threads and take processing throttle of one of each core ( bit weird :mad: )

---

### Post by mellowd on 2007-12-14
And it makes nice patterns too..

But flamelab is correct

---

### Post by Ink-Jet on 2007-12-14
Yeah, I get this too.
It's very strange.

---

### Post by pjkoczan on 2007-12-14
Also, the way CPU schedulers work, they take a process and assign it to the next available CPU. The next available CPU could be either core. It's nothing to worry about.

---


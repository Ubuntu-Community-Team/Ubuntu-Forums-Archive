---
title: "Why is it so slow for me?"
date: 2008-05-14
forum: General Help
---

### Post by tgilliam on 2008-05-14
i have ubuntu and xp dual booted...........Im new to linux, but why is it so slow. Is like this only at first? I think my CPU usage is high..how can i fix this and where is my hard drive :)

---

### Post by Het Irv on 2008-05-14
I'm gonna start backwards:

Hard Drive:  If you go in computer your Partition that has Ubuntu on it will be labeled "Filesystem"  The Partition with XP will be labeled as "45.5 GB Media" or something like that.

CPU: It might be the file tracker working that is giving you High usage.  You can change its setting in System->Prefrences->Search and Indexing

Slow: ehh.... slow how? While booting, opening programs, if so what programs?  What are your computers Specs?

---

### Post by tgilliam on 2008-05-14
512mb ram
2.79 celeron

like the interfaces are slow...when scrolling typing ect....doesn't take more than 5 secs to load a prog...but its slow when working

---

### Post by Het Irv on 2008-05-14
Your RAM is on the lower end of the requirement, and with the Tracker enabled and eating some of your RAM, I am not suppriesed that it is slow. Try going into Search and Indexing and turning of the tracker, then restart your computer to clear the RAM.  You should be a little faster.

---

### Post by rubicon on 2008-05-14
**Het Irv**, if he uses 8.04 then possibly tracker is disabled unless he turned it on on purpose. Trackerd was a problem for new users in 7.10, so it is disabled now in hardy.

And ram amount is quite enough to run Ubuntu smoothly (my case is proof ;) ).

**tgilliam**, check what uses your cpu in gnome-system-monitor, don't be so shy ;)

---

### Post by bingoUV on 2008-05-14
Symptoms look like bad graphics drivers. Which graphics card? Enabled restricted drivers (if Nvidia or AMD) ?

---

### Post by tgilliam on 2008-05-14
thanks for all the replies,its running smooth now :)

---

### Post by Het Irv on 2008-05-14
Ahhh, I thought It was still turned on by default.  Well there goes my happy feeling :lolflag:

I knew it was enough, but he is discribing something similar to a RAM shortage.  CPU usage is a good place to start.

---


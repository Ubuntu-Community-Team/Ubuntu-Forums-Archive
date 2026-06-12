---
title: "Performance problem - help appreciated"
date: 2007-01-19
forum: General Help
---

### Post by Michael Teofilov on 2007-01-19
Well I've been searching through different forums (in 3 languages) during a week without success, so I assume the right to ask for help :) The problem is kind of difficult to explain - my Ubuntu (6.06 - Dapper) seems to have dificulties with graphics like video clips and games - every second or so it stops for a very short time (like a tenth or less of a second) and then keeps on alright. This happens even with very low performance games, like Kobo Deluxe, so I am sure the problem is not with my hardware - with WinBoze all my games and videos work right. I installed the latest drivers for my graphics card but that doesn't seem to be the problem. If that helps, my machine is; Pentium 3/800 MHz, 512 RAM, i815 on-board chipset graphics card w/ 32 Mb video mem, 80Gb HDD, Sound Blaster 64 Live. Oh, and the MP3s and other music seem to work fine, but when I start a sound-editing program it suffers the same handicap - like the lmms linux multimedia system, so I really need to find a solution. Please give me a hand, all feedback will be very appreciated.

---

### Post by lamego on 2007-01-19
Try running the game without sound just to check if your issue is with the sound driver...

---

### Post by FluffyElmo on 2007-01-19
I don't know what the problem is, it may be a hardware driver issue or more likely there is a process that uses CPU/RAM periodically but you don't notice it until you put more load on your system. Try watching System Monitor while playing video and watch for any unusual activity when it skips. 

On your top menu it's under *System->Administration->System Monitor*. The *Resources* tab gives graphs which might tell you whether you're running out of CPU or Memory, watch for spikes coinciding with a skip. The *Processes* tab lists the running programs and can be sorted by CPU and Memory usage so if there is a misbehaved process you can narrow it down. You should select *All Processes* under the *View* menu item to also see system tasks.

You should also look at *System->Administration->System Log* and browse to see if there are any unusual messages that seem to coincide with your skips. You can also see any boot errors in the logs. They tend to be a little obscure but if any errors jump out at you that would be useful to know.

I'm off for the weekend, but if you post back what you find it may help narrow down possibilities and others may be able to chime in. Good Luck, I hope you get to the bottom of things soon since I know how frustrating these problems can be.

---

### Post by Michael Teofilov on 2007-01-19
> **lamego said:**
> Try running the game without sound just to check if your issue is with the sound driver...

yeah, I've tried that alredy - same thing. Seems like sound's not the problem... might be some background process that interferes all the time. I have a second hdd (2.5 GB) which is all swap, since I'm new to linux I don't know how it manages all the hardware so that could be the problem...

---

### Post by Michael Teofilov on 2007-01-19
>>Try watching System Monitor while playing video and watch for any unusual activity when it skips.

tried that - the CPU usage (in lmms for example) stays at 30%, and RAM usage is less than the half of the total available, that's why all the issue seems weird to me - I fell in love with Linux and Ubuntu in particular so I'd like to have it all in order (my girlfriend complains a lot about that skip thing). Believe me, I have tried a lot of things before I came here, creating a new account just to ask this question.

---

### Post by FluffyElmo on 2007-01-19
You may want to search for instructions on installing *GKrellM* and the *lmsensors* packages since they will give you a lot of hardware information. It can show graphs of hard disk usage/throughput as well as network usage for instance which would show if your disk is being hit or if a process is using the network when you have the problem.

It could also be a buffer problem, but since it happens with games and video and whether audio is on or not probably not. I'd say it's almost certainly some process that starts up periodically and uses CPU or disk though. Is Evolution checking your mail for instance?
 
In System Monitor are you even using any swap? If not then it definitely isn't the 2.5gb drive. If so then you might want to try putting your swap drive on a different IDE connector than your primary drive and setting it master. That's more of a random suggestion and I haven't done anything like that in years but I have seen it work way back in the day.

Sorry to type so much with so little help but I gather you're grasping at straws now anyways:)

---

### Post by Michael Teofilov on 2007-01-19
thank you very much for the continuous feedback, this is the first time I've ever asked anything on a forum (sems like I'll have to get accustomed to it with Linux :) ), I'm on it right now - installing the progs you suggested (gkrellm rules, thx) so I wish you a very happy weekend :KS  and I will post more info as soon as I get it. thanks for your time.

---

### Post by Michael Teofilov on 2007-01-21
OK, so gkrellm does show even peaks in the Proc and Hda2 (my ext3 fs) fields - so how do I learn what process(es) cause it? Tried messing up with the System Monitor and gave up after the 2nd restart :)

---

### Post by Michael Teofilov on 2007-01-22
alright, last bump to this one and I give up - been trying to find a solution for 2 weeks now...

---


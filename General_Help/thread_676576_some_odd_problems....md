---
title: "some odd problems..."
date: 2008-01-23
forum: General Help
---

### Post by Doom29 on 2008-01-23
Hi, feels a little odd my first post being one seeking help, but at the moment iv been having a few problems in general, and im not sure if they are related. My dad's current opinion is that I'm cursed >_>

1. most flash programs or flash oriented programs ( online video's and so forth ) either don't run properly, or dont run at all. For example: when visiting home star runner.com, I hear what their saying, then see it about 2 seconds later. with video's, it is more of a case of that if I attempt to adjust where the veiwing bar is, the entire video will disappear, meaning I cant fast forward. many video's ( such as those from meta cafe ) just wont run. I have macromedia and other required video players installed, but they seem unwilling to work properly.

2. random errors: The only one I can think of at the moment is having open office word processor crash and freeze on me. It wouldn't let me close out of it, and when I attempted to log off it only said that the file i was working on ( and it claimed i lost ) could not be recovered, thus preventing it from logging off as now every thing froze, forcing me to restart manually. 

I run into other odd problems here and there of things just not responding as i would like. which is odd, seeing as my dad has never encountered these problems in the year or so he has had Ubuntu compared to the week or two i have had it.

does any one have any idea's as to where my problems might be stemming from ? :confused:

---

### Post by ryanVickers on 2008-01-23
For the first problem, make sure you have all the latest video codecs and flash player installed.

PS - bit of cool info, in a total hang, instead of just killing the power, try holding "Alt + PrintScreen + R + S + E + I + U + B" (if thats too much, don't worry, the first few are usually enough :p)
It will make an attempt to shutdown properly reducing disk corruption chances - its not perfect but it usually works ;)

---

### Post by Doom29 on 2008-01-24
thanks :) 

unfortunetly though, I haved checked for updates on the latest flash players and it seems to be the lastest there is. I'll look into the video codec's next.

---

### Post by codybuntu on 2008-01-25
> **Doom29 said:**
> thanks :) 

unfortunetly though, I haved checked for updates on the latest flash players and it seems to be the lastest there is. I'll look into the video codec's next.

In Firefox address field type about:plugins. This will list all plugins installed in firefox. Now check if you only have one flash plugin isntalled. I had similar problem and I found out that I had 2 flash players installed one was in the system installed by synaptic and other was in my home/.mozilla/firefox directory. So I hust removed the one in the home directory and everything works fine now.

---

### Post by Doom29 on 2008-01-29
I checked the plugins, the only two I have installed that MIGHT conflict are java and shockwave. but I doubt its those.

---


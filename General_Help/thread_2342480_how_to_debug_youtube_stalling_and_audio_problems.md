---
title: "how to debug youtube stalling and audio problems?"
date: 2016-11-07
forum: General Help
---

### Post by joshua-downer on 2016-11-07
I may have two problems here, but I am not sure. I have had audio problems for a long time now. More recently I have been unable to successfully play video on youtube (on both firefox and chromium). I am on ubuntu 14.04 and I use the Qtile window manager.

The main problem I have had with audio is that I get no playback when I use the headphones. That's a problem because that is primarily how I want to hear audio. I have tried numerous tweaks to address the problem. The result is that I have made a bunch of changes to a system that I don't really understand, and now I don't know if the original problems persist or if I have introduces new ones. I don't know how to debug audio on linux. More than anything, I would like some guidance on how to solve this problem for myself. I have played around with pavu, pactl, alsamixer, amixer, configuration files... nothing has fixed the problem and now I don't trust the state of the system. Can anyone provide advice on how to debug audio?

The other problem is video playback. It is a problem on both firefox and chromium so I don't think it is necessarily a browser issue. In both cases the video starts to load but then seems to stall. Confusingly some, rare, video do play. Also, firefox (I normally use firefox so I don't know if this is also an issue on chromium) seems to frequently hang, and I suspect it is due to embedded video. I may be paranoid, but I have a suspicion that the problem is caused by the problems that I am having with audio. I have tried running the browser in debug mode, but there is no information about the stalling or any other problem that might suggest a cause. As above, I would really appreciate some advice on how to approach and debug the problem.

-Josh

---

### Post by gordintoronto on 2016-11-07
You have not received an answer, probably because people see "qtile" and say to themselves, "then I can't help." This is not a criticism of Qtile, just a comment about leaving the mainstream.

Problems with playing video are often related to hardware specs, so providing that information might help: CPU, memory, video adapter, "additional driver?"

---

### Post by joshua-downer on 2016-11-08
Thanks for the feedback! Yeah, I mentioned qtile just because I didn't want people to waste their time with advice like "go to the system settings..."

I can absolutely provide the specs you have requested, but I am not sure that it is related to the hardware because audio and video have worked in the past, and worked for a while. So I don't think it is likely to be a driver issue, although you could be right -- I am not an expert in this :)

---

### Post by joshua-downer on 2016-11-08
Actually -- thinking about it more -- mentioning qtile is a red-herring. There is no reason why I cannot login to a standard desktop if it provides a way to better understand these problems.

---


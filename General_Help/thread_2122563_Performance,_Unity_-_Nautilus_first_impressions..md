---
title: "Performance, Unity - Nautilus: first impressions."
date: 2013-03-05
forum: General Help
---

### Post by greenwom on 2013-03-05
I've actually been off ubuntu since 12.04, I'm back and I'm somewhat diappointed.  

I have the common complaints of the amazon adds, "for purchase" apps, and privacy issues.  I've dealt with most of that, Canonical needs to really rethink these issues.  I really don't want to be forced to have a entire "bloat ware" removal session every time I reinstall (sounds like another OS).  Anyway.

[B]
the problem now is performamce.[/B]  

Here's the list. 
1.  When lunching applications from the launcher, there is a lag.  Noticiable and there's no feedback or response to say "I'm busy".  Leaves you not knowing what the computer is doing.
     Once the apps are open switching isn't an issue.  

2.  Nautilus is extremly slow.  Large folders or small, the window pops up and doesn't populate.  Making the file browsing experiance painful.  I've watched for a memory leak on this but haven't seen anything.  

I'm running the 64bit version of 12.10 on HP DV71170us.  It's got a 2 GHz Intel Core 2 Duo Processor T5800 and 4 Gigs of ram and I have the Nvidia drivers loaded.  
So I'm not sure why these perfomace issues are happening.  I've had much better results on older laptops.  

Any suggestions to improve this?

---

### Post by kclark on 2013-03-05
Are you married to the idea of using the default WM?  I use XFCE + cairo-dock + conky and have been very happy with it.

---

### Post by greenwom on 2013-03-05
> **kclark said:**
> Are you married to the idea of using the default WM?  I use XFCE + cairo-dock + conky and have been very happy with it.

I'm not married to it, I try to go with the flo for the most part.  when I installed 12.04 I went with gnome3 and was happy. 

I just don't always have the time to configure anymore (kids will do that to ya :) )

I also have high expectations, I've used Ubuntu since warty and never had this poor performance from the base system (not to mention the privacy, amazon, and software center add-ons).

---

### Post by sanderj on 2013-03-05
Did you do a fresh install, or an upgrade?

My experience: 
1) upgrades result in slow systems. 
2) 12.04 was slow, 12.10 was better, and 13.04 is really fast (all on my Samsung laptop: Intel Core i3-370M (2.4GHz), 4GB DDR3 RAM and Intel GPU)

---

### Post by rnerwein on 2013-03-05
hi
i guess your problem is in the organisation of your directories. it depents even on what you are running on the system. an access (if it is read/write) by concurent application is atomic (means the directory is locked - it must !). if a file-browser needs to much time for you - think about your directory structure. 
e.g.: start-point/subdir a,b,c,d and so on. but your apps have this to manage too. i apprecitate you have a lot of folders in your directory. even you get bitmaps inside. for me, i have a 10 years sony with blitter chips - faster than hell for graphic - and it's in this folders faster than a new 4 core amd !
last at least - it depends on the strategy and the hardware you use - not on the system (mostely ;-)  )
ciao

---

### Post by kclark on 2013-03-05
> **greenwom said:**
> I'm not married to it, I try to go with the flo for the most part.  when I installed 12.04 I went with gnome3 and was happy. 

I just don't always have the time to configure anymore (kids will do that to ya :) )

I also have high expectations, I've used Ubuntu since warty and never had this poor performance from the base system (not to mention the privacy, amazon, and software center add-ons).

Yeah I don't have much time for configuring like I used to.  But in all honest sudo apt-get install xfce cairo-dock then auto start cairo-dock at login and remove the horrible dock that it comes with.  Shouldn't take more than 15 minutes.  I'm verry picky also.  Conky is the only thing that takes me a while just because I want a specific output and look.

---

### Post by greenwom on 2013-03-05
Fresh Install. 
the directory structure is pretty straight forward.  Music -> Band -> Albums -> songs

Again performance has never been an issue before.  

I've tried XFCE on my old Dell mini 9 and it works well, I'm also picky and had to give up on conky (could never get it to look just right :)

---


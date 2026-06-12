---
title: "Beryl crashes and stops working"
date: 2007-09-25
forum: General Help
---

### Post by farazq on 2007-09-25
Hi Guys,

I'm a newbie to Linux and Ubuntu 7.04 (Feisty) and i've just been playing around with the OS and the process of installing applications etc. I came across beryl on an interesting pcworld article ([http://www.pcworld.com/article/id,130923-page,1-c,linux/article.html](http://www.pcworld.com/article/id,130923-page,1-c,linux/article.html)) and thought i'd give it a go. I installed it fine and started to make customisations, but at one point beryl seemed to crash and everything on my desktop froze, all i could do was move the mouse. When I rebooted I found that beryl-manager would load OK but when I tried switching to the beryl window manager, nothing happened and it simply switched back to metacity (gnome). If i tried to enable Desktop Effects, my machine would slow down drastically and freeze. I've been trawling through forums and threads trying to figure out what the problem was and how to fix it and I think I've solved it, but I thought I'd post on here to see if anyone can make sense of it and also so it could help people having a similar problem.

The process I followed was:

[LIST]Completely remove beryl and associated components using Synaptic[/LIST]
[LIST]Go to my /home/<user>/ directory and remove the .beryl folder and the filename which contains the word beryl (Sorry I can't remember the exact filename - i'm not at the computer), I also removed the .emerald folder in case.[/LIST]
[LIST]Restart PC[/LIST]
[LIST]Follow the procedure to install beryl on the PC World article (link above)[/LIST]

This fixes the problem for me - the cause seems to be very strange though. I noticed that when I tried to change the cap images on the desktop cube, and also add the skydome image, beryl crashed and I had the same problem again. I remember when it first crashed I was attempting the same thing; trying to change the cap and skydome images, so I don't know if the cause is actually something else but looks like this or whether it is actually related to the images...can any experts shed some light?

Thanks and apologies if this has been posted before.

---


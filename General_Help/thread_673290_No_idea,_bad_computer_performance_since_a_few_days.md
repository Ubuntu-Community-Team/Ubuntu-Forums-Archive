---
title: "No idea, bad computer performance since a few days, maybe nautilus"
date: 2008-01-20
forum: General Help
---

### Post by Birk on 2008-01-20
Hi,
I tried to solve this problem by searching other posts and google, but could not quite find the answer. Sorry for the lengthly text following, but I try to give as much info as I know that might help solve this.

After I installed ubuntu 7.10 on my new Laptop (Dell Vostro 1500) and getting (nearly) everything working nicely, I started playing a little bit around with the appearance.

The computer was running nice and fast before the last tweaks and never crashed for about 2 weeks.

During all the time of installing and configuring my laptop I extra only installed things with "add/remove applications" or the "synaptic package manager", because I was afraid to mess something up otherwise. The only thing not installed from there is matlab and mathematica. 


The last thing I recalled have done was installing "desktop drapes" and "wallpaper tray" (both are programs to manage the wallpapers) and changing the login screen in "System/Administration/Login Window", but I have changed everything back again.
[U]
So now to my problem:[/U]
After the last installations I suddenly could not access a few things anymore, like the "Log off switch", which seemed dead and the right click on the desktop did not do anything anymore either. Other programs seemed to work fine though, e.g. thunderbird opened ... .I checked the running processes with the system monitor, top and htop (a slightly more convenient version of top) and all gave different total cpu usages ( I have a intel 2 duo 2.00GHz processor)

After looking a little longer it seemed that:
nautilus --no-default-window --sm-client-id default2
took more resources than it should (by the way is all the stuff on the right good or bad?)
So I killed it and suddenly I could access everything again. 

But from then on I got all kinds of problems with the next restarts of my computer. Sometimes I think the cpu's are just used too much (both at >50% for no reason) sometimes programs would not start, or the computer would crash without a way to recover it (no keybord or mouse response, no CTRL+ALT+F1, no restart xserver...).
I tried to reproduce the problems, but I still don't know what is the problem and which combination of programs gives trouble. Today I played a little bit around but everything seems to be working fine for about 2 hours. I tried to find in the internet if others have the same problem, but did not find much more than following thread:
[http://ubuntuforums.org/showthread.php?t=595241](http://ubuntuforums.org/showthread.php?t=595241)

I appreciate  any hint, for what to even look for. I would be glad to give more info on questions, off course. I don't know too much about linux though so be easy on me, please.

thank you

---

### Post by AlanR8 on 2008-01-20
You said it was a fresh(ish) install on a new laptop. 

I would suggest you try a complete re-install, it only takes about 20 mins and start again! See if the problems happen again.......

---

### Post by Birk on 2008-01-20
I thought about this myself.
Unfortunately I put already quite some time getting everything ready (>10hours), especially since the vostro had some problems with the sound and I would rather not do this. And of course there is also the point, that it would just be so much nicer, if this could be solved by not just reinstalling the system (isn't this one of the big reasons to not use windows? ;) )
But yes, if this keeps on being a problem I will do this. Of course, than I won't know which part of my configuration caused all this and am likely to run in this problem again,

Birk

---


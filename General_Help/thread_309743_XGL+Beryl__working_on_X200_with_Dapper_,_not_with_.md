---
title: "XGL+Beryl  working on X200 with Dapper , not with Edgy -- hard locks"
date: 2006-11-30
forum: General Help
---

### Post by 89camarorsv6 on 2006-11-30
hello,

This is really driving me up the wall. I originally had XGL, beryl with fglrx driver working perfectly on dapper. Then I upgraded to edgy, now I installed beryl from ubuntu2 repository (0.1.2) and also tried trevors 0.1.3 SVN rep.

I had originally set it up similar to the wiki article (when I was running Dapper, Edgy still runs the same config.

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL)

When I log into the Xgl Desktop Session, using startxgl it just hangs / hard locks.

I have done the following

1. Reinstalled Xgl,
2. Reinstalled fglrx
3. Reinstalled beryl like 100 times with different repositories and versions

It always ends up in a hard lock. I can go into regular gnome and fglrx is working as fgl_glxgears work as well as fglxrxinfo.

Can someone shed some light here?.

I have also tried the thread with X700 fix for Xserver

[http://ubuntuforums.org/showthread.php?t=150854&highlight=xgl+hard+lock](http://ubuntuforums.org/showthread.php?t=150854&highlight=xgl+hard+lock)

That doesnt work either. 

What I know works for sure

1. Xorg Acceleration with fglrx as I can play games and glxgears etc.
2. I can start Xgl from a terminal window in regular gnome on Desktop :1 and it starts fine.
3. Beryl Manager Icon comes up fine on the gnome regular session.


Specs:

Compaq Laptop Presario 2200M
ATI X200M Graphics 

Thanks

---

### Post by shanepardue on 2006-12-04
I'm having the same problem. Ubuntu loads up fine, but when I run the 
command "beryl-manager", it hard locks. The latest Nvidia driver gives 
me poor refresh rates, no matter what workaround I try. AIGLX is not an 
option. 

Are we stuck with the latest Nvidia driver and AIGLX on Edgy?

---

### Post by 89camarorsv6 on 2006-12-05
Shane,

I only have this problem on my ATI laptop. I have a desktop with 7900GTO on AMD64 running Gentoo with the Beta Nvidia Drivers and AIGLX beyrl runs like a charm.

ATI doesnt support AIGLX on FGLRX from what I understand. thats why Xgl.

---

### Post by shanepardue on 2006-12-05
I'm running Nvidia, but I've managed to get AIGLX running decently. Still a little choppy, but it'll have to do. Maybe they'll fix it soon.

---

### Post by azidrane on 2006-12-16
Hey mate,
Until the 8.32.5 ati drivers came out recently, the only way to get beryl running on a x200 ati card was to use
[LIST]
[*]-ati 8.24.5 or in some case (like my own) 8.26.5
[*]-ubuntu 6.06 (dapper)
[/LIST]

This is due to the fact that edgy (6.10) has Xorg 7.10 or whatever installed, while dapper has the older version. The new version enables direct acceleration as part of xorg while the old one does not and needs an overlay. this card only works with the overlay (xgl) and tahts about it.

Now, don't quote me on this when it comes to 8.32.5 because I havn't  tested it with edgy yet. I am, however, running these drivers in dapper right now and it's working like a charm. MUCH faster and smoother then the old drivers. AND you don't have to enable the shared RAM like before (sideport error in the old drivers)

Anyway, if you'd like a hand, PM me and maybe we can work through it. I've been fairly successful in setting this up on three differant ATI machines.


If you want to try out the new drivers, try this (*its a script i found on the net. the dapper one works like a charm*):

```

wget http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh

sudo chmod a+x ati-8.32.5-builder-edgy.sh

sudo ./ati-8.32.5-builder-edgy.sh

```

then reboot. If you do, please post your results.

Cheers!


EDIT: Here is a link to another post related to this subject : [http://ubuntuforums.org/showthread.php?t=318889&highlight=200m]("http://ubuntuforums.org/showthread.php?t=318889&highlight=200m")

---

### Post by hollerith on 2007-01-12
Works on advent 7105pa.  Noisy fan though!

---


---
title: "xgl as a 'session'"
date: 2006-07-05
forum: General Help
---

### Post by Zyphrexi on 2006-07-05
i'd like to be able to choose between xgl/compiz and regular X for when I play games, how do I do this? Normally I end up re-editing all the config files back to the original state, but that is sorry to simply play games.

---

### Post by XAsmodeanX on 2006-07-05
[http://www.ubuntuforums.org/showthread.php?t=174233]("http://www.ubuntuforums.org/showthread.php?t=174233")

Enjoy.

---

### Post by bluevoodoo1 on 2006-07-05
Try this...
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

You'll have to return your gdm.conf file (and/or your gdm.conf-custom) back to the way it was before editing it for Xgl.

---

### Post by bluevoodoo1 on 2006-07-05
[QUOTE=XAsmodeanX][http://www.ubuntuforums.org/showthread.php?t=174233]("http://www.ubuntuforums.org/showthread.php?t=174233")

Enjoy.[/QUOTE]

Use [http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29) instead. It's easier by a few steps. And I use that (rather than the above link)

---

### Post by Zyphrexi on 2006-07-05
maybe i'm not doing it right... but it doesn't seem to be working


EDIT: my mistake, it's working fine now.

YOU ARE THE *MAN! It's just what I wanted.

(*man/men/woman/women/robot/space-alien/wombat/drake/eft/etc)

---

### Post by pRedat0r on 2006-07-05
Are there any differences for those of us that are using ATI cards, or should this tutorial work work either nv or ati?  I followed a nearly identical tutorial (without the xmodmap part, but with identical code in the scripts besides that) and I get messages that my session lasted less than 10 seconds, and in the xsession error log it displays for me, it tells me it cant find any screens.  By the way I did update the timeout in gdm.conf for 50 seconds and did a full reboot and that made no difference.

Any help would be appreciated, I like the idea of a separate session as well, but dont see any additional settings that ati users need to do, while on the other methods i see updates to the gdm.conf to set the screen on display 1, etc, etc.

Not sure, but I have 2 monitors as well on the same card (ati 9800 pro), anyone with an ati card running in the "big desktop mode" have XGL working?  Maybe it just doesnt like running in that mode, i might switch off the 2nd monitor or try clone mode and see if that helps..

Edit: also, I am running the fglrx 8.25.18 driver provided in the repos..

Thanks.

---

### Post by Zyphrexi on 2006-07-05
I don't know much about that question, but I found this and I think it's a pretty good solution.
[http://www.compiz.net/viewtopic.php?id=1615]("http://www.compiz.net/viewtopic.php?id=1615")

check out the picture in the listing to see what it does. It looks pretty darn cool.

---

### Post by Anduu on 2006-07-06
[QUOTE=Zyphrexi]I don't know much about that question, but I found this and I think it's a pretty good solution.
[http://www.compiz.net/viewtopic.php?id=1615]("http://www.compiz.net/viewtopic.php?id=1615")

check out the picture in the listing to see what it does. It looks pretty darn cool.[/QUOTE]

Right now I have Xgl set up as a seperate session but this looks hella cool!

Thanks for the info :cool:

---


---
title: "Composite disabled =&gt; X disabled"
date: 2007-02-15
forum: General Help
---

### Post by Dragonstar on 2007-02-15
Here's my problem. My X won't start if I put "composite disable" in my xorg.conf. When login screen should come up, all I get is a black screen and whole system freezes. Can't use ctrl+alt+f1 or anything. Only reset my whole computer. I need that "composite disable" to have DRI.

This is the second time I have this problem. At the first time the only solution I found was to reinstall ubuntu, but I had to cut off my network connection before the install for X to start properly after the install. After that install I got dri working just installing fglrx from synaptic. After that I didn't update anything I though could broke my system again. But still after few weeks when I first time shut my pc down for the night, it didn't work at the morning. X didn't start. With vesa-drivers I got X running and updated everything update-manager suggested. But it didn't help, X didn't start with fglrx-drivers and composite disabled in xorg.conf. I also tried older version of fglrx I found from synaptic, but no difference there.

Another strange thing is that if I try to start my pc from edgy live-cd, it does the same thing. Black screen after that loading ubuntu logo.

This problem has now two times "rised from nowhere". First time it came up when I started my pc after a 3 week holiday (don't remember if I had made any updates before that holiday) and now second time. After that first time I don't think I updated anything that could be connected to my video drivers. Of course I don't know what every package I update does, but I didn't update anything like xorg.something.

Here's my [Xorg.0.log]("http://draspu.user.fi/Xorg.0.log.old") and [xorg.conf]("http://draspu.user.fi/xorg.conf") for the time my X freezes. Strangely in the Xorg.0.log there's no errors (EE) anywhere. And [here's]("http://www.ubuntuforums.org/showthread.php?t=359132&page=3") a link to a thread where I already got some help (thanks to IgnorantGuru :)), don't know how to link straight to my post sry, it's the third from the top.

First I thought that my video card is broken, but because my windows has worked fine all the time I guess it's not that. But then what is it? Something wrong with the drivers or what? I'll appreciate any help you guys can give.

Ubuntu 6.10
AMD Athlon 64 3200+
1GB RAM
ATI Radeon 9800 Pro 128mb

---

### Post by dcstar on 2007-02-15
> **Dragonstar said:**
> 
........
First I thought that my video card is broken, but because my windows has worked fine all the time I guess it's not that. But then what is it? Something wrong with the drivers or what? I'll appreciate any help you guys can give.

Ubuntu 6.10
AMD Athlon 64 3200+
1GB RAM
ATI Radeon 9800 Pro 128mb

There are a multitude of posts in the forum in recent weeks from people who have had various video problems since some recent updates were released, I suggest you search them out to find a solution for your particular hardware.

---

### Post by Dragonstar on 2007-02-16
> **dcstar said:**
> There are a multitude of posts in the forum in recent weeks from people who have had various video problems since some recent updates were released, I suggest you search them out to find a solution for your particular hardware.

I wouldn't have made a new topic if I hadn't already searched the forum for help.

Almost every post suggests to install correct modules/build your modules manually/update drivers/install drivers manually/reconfigure xserver-xorg. I have already tried all of those and nothing worked. Also I had this problem for the first time before this recent kernel update, so I don't think it's because of that.

---

### Post by Dragonstar on 2007-02-18
So noone knows anything? Do I really have to reinstall once again and stop updating anything? :(

---

### Post by Dragonstar on 2007-02-18
Thanks for your help guys. The answer to my problem came from a person with another distribution with nvidia video card, pretty strange don't you think. Maybe I need to think again my choice of distro...

Anyway the solution to my problem was to add the following to the module section of xorg.conf:

```
    SubSection  "extmod"
        Option  "omit xfree86-dga"
    EndSubSection
```

Hope this helps someone else with the same problem. :)

---


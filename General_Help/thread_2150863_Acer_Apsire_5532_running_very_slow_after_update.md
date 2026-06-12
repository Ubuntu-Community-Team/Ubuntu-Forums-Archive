---
title: "Acer Apsire 5532 running very slow after update"
date: 2013-06-02
forum: General Help
---

### Post by ghost25 on 2013-06-02
Greetings, all. I recently re-aquired my old Acer laptop (granted, with older hardware) and figured I'd give Ubuntu 12.04 a try, seeing as how 10 is no longer officially supported.

While I do like some of the features of it, one of my biggest annoyances is one that I suspect a lot of users may be encountering. Simply, my computer is slowed to practically a crawl. While everything loads and, if not X11-supported (ie Terminal), runs smoothly, as soon as I have to use X11 or any accelerated graphics I notice that the entire thing slows visibly. Graphically, it's almost unusable. My internet is a decent speed for me, however pages seem to take forever to load, and sometimes fail. I suspect this is because the graphics just can't load fast enough and in this day and age graphics are as essential as having the proper XHTML coding.

Anyway, here's what I'm wondering. I've done some Google sleuthing and, while I have found one or two articles that slightly helped (emphasis on "slightly"), my computer still seems to be performing like a mid-90s desktop that thought 128MB of RAM was high-powered. Can anybody tell me of any tweaks that I could use, like turning off eye-candy or something, that would make it so I can at least use this machine instead of my higher-powered desktop rig for daily use? I don't really need any of the fancy doodads or widgets or anything, I just want to be able to use it and not have to type in a web address, go drink a cup of coffee and smoke a cigarette, then come back and hope it's done processing?! Any help on this count would be greatly appreciated.

Oh and I would include command outputs here but I don't really know what would be needed so, any outputs you need just ask, I'll get them posted after 3:00 PM CST. I'm very comfortable with Terminal so that's no problem. Thanks in advance.

---

### Post by maglinu on 2013-06-02
Just a thought - have you tried unity 2d option at login?

---

### Post by techvish81 on 2013-06-02
you can try xubuntu or lubuntu rather than ubuntu which is designed for newer pcs with better specs. lubuntu would be the lightest of all in the ubuntu family.

---

### Post by DeMus on 2013-06-02
When you write: [COLOR=#000000]Simply, my computer is slowed to practically a crawl do you mean this or does it just looks like it?
I ask this since I had the same and with my computer it turned out that akonadi opened I don't know how many instances which filled both the physical memory and then the swap too, plus the processor was used at 100% all the time.
I re-installed Kubuntu 13.04 and now it is okay. No idea what went wrong, but using the computer then was impossible.[/COLOR]

---

### Post by ghost25 on 2013-06-02
@DeMus No, I mean that it becomes unresponsive after a while; when a web page is trying to load in Chrome, for example, the loading icon instead of spinning smoothly like usual is very jerky. Everything else takes forever to load or do what I want.

I haven't tried Xubuntu or lubuntu, I've only ever used the normal Ubuntu flavor. I'm not sure I want to switch to a cousin OS because everything I need transfered seamlessly from 10.04 to 12.04, its just the performance that's lagging. As far as Unity 2, I'll give that a try right now and get back to ya, let ya know how that worked for me.


EDIT: I did switch to Unity 2d, and it does indeed seem to speed up computing time. Thank you much, I'll see how well this continues to work.

---

### Post by maglinu on 2013-06-03
Good. Something else that might well help is decreasing the swappiness value.
[https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

---


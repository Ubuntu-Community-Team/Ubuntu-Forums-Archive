---
title: "Animate windows to top when I have panel at top"
date: 2014-01-18
forum: General Help
---

### Post by matospalka on 2014-01-18
Hi everybody, 

I need some help - in my Lubuntu - i have one panel at top and one on the left side.

When I minimize window, its going down - but there I dont have panel - I dont like it. I would like to minimize window to the top (i mean the animation of the window, when its minimizing...).

Is there any kind of options to change it?

Thanks for you help!

---

### Post by matospalka on 2014-01-19
Nobody knows?

---

### Post by matospalka on 2014-01-28
I dont know how to do it, a spend with that a lot of time...

---

### Post by vasa1 on 2014-01-28
I just saw your thread. Different time zones ;)

BTW, could you mention your CPU/RAM?

If you find the animation undesirable, just turn it off by editing your **lubuntu-rc.xml**: search for **<animateIconify>yes</animateIconify>** and change **yes** to **no**.

My feeling is that the animation effect is not specific to Lubuntu but something related to Openbox, which is the window manager Lubuntu uses. On the other hand, it is possible it somehow (I don't know how) is related to the type of panel. While the default Lubuntu panel is lxpanel, I'm using something else called **tint2**; with tint2, I can see the animation compacting to the parent icon in the toolbar and expanding from there to where the window will be position when I "restore" the window.

---

### Post by vasa1 on 2014-01-28
I googled for "direction of animation in openbox" and the first hit (from **2010**) pointed to this: [OpenBox iconify animation]("http://forums.debian.net/viewtopic.php?f=6&t=53601"). Quoting from there:
> I have noticed that when I use **tint2** panel in openbox, the openbox iconify animation moves **downwards** regardless of where the panel is placed, however when I use **xfce4** panel, the direction of the iconify/minimise animation is towards wherever the panel is located, ...
So it seems the choice of panel somehow makes (or made) a difference!

As I said, currently I'm on tint2 (the version in the repos) and have it located at the top: the animation is upwards. I haven't tried other positions. Too lazy ;)

Edit: here's another similar complaint (2009) about lxpanel: [http://crunchbang.org/forums/viewtopic.php?id=718](http://crunchbang.org/forums/viewtopic.php?id=718)

Maybe I'll give it a try as well and post back.

Okay, I just logged into a Lubuntu session with lxpanel at the top. The minimizing animation points down as if the panel was at the bottom. My system is fully updated and so I'm guessing this is a feature (aka bug) of the current lxpanel/LXDE/Lubuntu.

---

### Post by vasa1 on 2014-01-28
> **matospalka said:**
> Nobody knows?
I'm really sorry about that. I don't know how your question remained unanswered for so long. But my suspicion is that there aren't that many Lubuntu users around anymore ;)

If you have any further questions, please feel free to PM me with the link as soon as you've posted a question in the forum and I'll do my best to help or search for help.

Another trick you can try is to use the tags feature: so tag your question with "lubuntu", "lxde", and "openbox" (as appropriate).

Yet another thing you can do is to bump your post after every +24h if possible. It's allowed here. I wrote **+24** so that a different set of people may see your question.

All the best.

---

### Post by vasa1 on 2014-01-29
While my OS is Lubuntu 13.10, I prefer running the Openbox session instead of Lubuntu session. In the Openbox session, I use tint2 as my panel. And I just checked the animation on minimizing/maximizing: the animation properly follows the location of the panel, unlike what you and I see with lxpanel.

---

### Post by matospalka on 2014-01-30
So it is a bug? If so, then I can do nothing with that. OK, I will keep my LXpanel on the bottom and hope, that somebody will repair this bug... Thank you very much...

---


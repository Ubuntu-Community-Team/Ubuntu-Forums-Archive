---
title: "xorg issues"
date: 2007-05-31
forum: General Help
---

### Post by mrtrick on 2007-05-31
I've been working for a few days on getting WoW running in wine. This has involved installing updated drives for my video card. At one point I used Envy (which I don't recommend) and it completely hosed up my system by half implementing a kernel module and comlpletly screwing up my xorg.conf file. Got it all fixed, but during the process I had  a thought. . . 

These types of issues are exactly why people do not adopt Linux / Ubuntu. Most people would have gotten into a situation like this and walked away (Back to M$). 

Why can't there be some sort of failsafe that if x can't be started, it asks if you would like to run dpkg-reconfigure xserver-xorg to at least get back to a default drive that will desplay GDM (or your desktop of choice)?

Thoughts?

---

### Post by EndPerform on 2007-05-31
That's the reason third-party scripts such as Envy aren't supported, they can cause issues such as the one you experienced.  Normally for me, I install the latest beta drivers and whatnot by hand so I know exactly what is going on with my box.

I usually keep a failsafe config file lying around.  In my case, I know the 'vesa' driver works if I ever run into a situation where my nVidia driver fails and I need X.

---


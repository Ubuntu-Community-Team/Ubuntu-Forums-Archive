---
title: "Gutsy dual monitors with a 19&quot; and 15&quot;"
date: 2007-10-20
forum: General Help
---

### Post by PricklySponge on 2007-10-20
Hello. I have 2 monitors, my 1st is a 19" wide screen, and my second is a 15". I'm trying to set up the dual monitors to a similar fashion to how they are configured on my windows partition

[IMG]http://i3.photobucket.com/albums/y80/PricklySponge/whatiwant.jpg[/IMG]

What goes wrong, is when I use the dual monitor utility built into gutsy, my 19" primary screen is oddly run in some sort of zoomed in mode. Is there any way that I can set up my monitors to a similar fashion as to how they are in windows? This means thats I would like all my task bars, and things of that nature on my 19" primary screen- using my 15" secondary screen purely as blank storage space.

Thanks :)

---

### Post by PricklySponge on 2007-10-20
Anyone think they could help me out?

---

### Post by sinn on 2007-10-20
> **PricklySponge said:**
> What goes wrong, is when I use the dual monitor utility built into gutsy, my 19" primary screen is oddly run in some sort of zoomed in mode.

Theres a dual monitor tool?

I have the same monitor setup as you. Mine is a 15 inch LCD max 1024x768 and the 19 inch is CRT at 1280x1024.

I have had nothing but problems with getting these monitors setup properly. And i am not skilled enough to write my own xorg.conf, I tried and ended up reinstalling.

---

### Post by ihcnet on 2007-10-20
I've always found the Gentoo Wiki really helpful when configuring dual monitors. Check it out:

[https://www.worldofwarcraft.com/account/resurrect-a-friend.html](https://www.worldofwarcraft.com/account/resurrect-a-friend.html)

---

### Post by sinn on 2007-10-20
that doesn't look like a link to the Gentoo wiki....

---

### Post by sinn on 2007-10-20
that doesn't look like a link to the Gentoo wiki....

---

### Post by seventyeights on 2007-10-20
[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

---

### Post by sinn on 2007-10-20
any idea of how i could get daul monitors to begin with? i found the screen and graphics preferences but only one monitor shows in there, and it shows the monitor that isnt active

---

### Post by ihcnet on 2007-10-20
Thanks seventyeights, I guess I had the wrong link in my clipboard. :lolflag:

---

### Post by PricklySponge on 2007-10-20
I looked at the gentoo wiki and its mostly about how to set up twinview. But isn't twin view what the dual monitor tool uses. In which case, wouldn't I still have the same problem?

---

### Post by burningbed on 2007-10-21
I have had a perhaps somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

---


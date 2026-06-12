---
title: "XGL Problem (EXTREMELY low FPS)"
date: 2008-05-11
forum: General Help
---

### Post by Ace (SWE) on 2008-05-11
So I just got Ubuntu 8.04 not too long ago and it's really slow.
I tried running "glxgears" just to see what my FPS was, the result?
50FPS (used to get over 5000).

I've been using Linux for quite some time now and I have no idea why this happens.

Specs:
AMD Athlon 64 3500+
1GB DDR PC2700
ATI Radeon X1650PRO

(I'm using x86 and yes, I've installed the proprietary drivers)

---

### Post by ajmorris on 2008-05-11
you could always switch back to AIGLX instead of XGl... it would increase dramatically

---

### Post by ibargureni on 2008-05-11
I also had those problems after upgrading to 8.04 my laptop with a Ati x1400 graphics card. I couldn't find the exact combination of window manager and driver till I read I could use AIGLX instead of XGL with the drivers included in this distribution. To use AIGLX I just uninstalled XGL from synaptic. With that everything came back to what it used to be.

After a bit of using it I have realized AIGLX is much, much better than XGL, since lots of aplications that didn't work with XGL work correctly now (e.g.: AWN).

However, I am having a problem with some graphicaly intensive aplications, mostly games (Torcs, Urban Terror, GoogleEarth, etc.) since they seem to flicker a lot, but reverting to metacity when I use those programs solves the problem (metacity --replace). It's not completely straight forward but these programs simply didn't work with my previous configuration. In addition to this, I have recovered Suspend and Hibernate with Hardy, so I consider it a great upgrade.

I hope this helps,
regards.

---


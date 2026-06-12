---
title: "Transparent dock without compiz"
date: 2007-12-08
forum: General Help
---

### Post by daspooky on 2007-12-08
Hello fellow Ubuntu users,

I'm looking for some dock-application with a completely transparent background, but without the need for a compositor (like compiz or the xfce compositor).

I'm running xubuntu Feisty, my graphics chip is an intel i915 (kind of slow with compositing enabled + video's play in black when using xvideo, using X11 is not an option as too slow and jaggy edges). 

So to summarize: is there an application out there which can place png's on my desktop, without a background, and without a need for compiz of another compositor?

Thanks all.

Greetings,

daspooky

---

### Post by daspooky on 2007-12-11
Well, to answer my own question.. one word: wbar

---

### Post by ravenon on 2007-12-11
Wbar is an interesting app. Have you managed to get it to start with the session? I can, however I lose transparency of the bar.

---

### Post by zach12 on 2007-12-11
It looks like the gdesklets dock

---

### Post by daspooky on 2007-12-13
> **ravenon said:**
> Wbar is an interesting app. Have you managed to get it to start with the session? I can, however I lose transparency of the bar.

I start it this way: wbar -above-desk -pos bottom -j 1 -balfa 0 -isize 90 -zoomf 1.4

Check out the balfa parameter, I believe this is used to control transparency

---


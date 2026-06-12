---
title: "Nautilus/Gnome Very Slow"
date: 2004-11-15
forum: General Help
---

### Post by maus on 2004-11-15
I installed a custom, processor-optimized 2.6.9 kernel not too long ago, and have been pretty happy with most of what it's done for me (hell, even if it's a placebo effect). I was using the i386 kernel, and I'm now on a k7 kernel that supports some of my more esoteric hardware that the main kernel didn't. So. That's nice.

Anyway, everything's pretty keen, except that Nautilus (and Gnome in general) runs much, much more slowly. I can't count on clicking on one of my desktop folders and having it come up almost instantly, like it did pre-custom-kernel.

I'm using the same video drivers I did last time, and I *think* I have DMA enabled on both of my hard drives... the 80 GB that Ubuntu lives on, and the 40 GB that my ~/  lives on. 

But I might not. I can't figure out how to activate DMA. I recall there being a dialog somewhere that let me enable DMA mode, but to no effect; every time I go back, it's unchecked. Is there a config file I need to look at?

Or is this being caused by something else? All of my RAM is registering, and I'm running the exact same hardware I did pre-kernel compile (Athlon XP 2000+, 640 MB RAM, it is a MEAN MACHINE... from 2001). 

I'm also noticing that it takes a little longer to open up the ~400 MB video files I watch from time to time, but once they're up, xine's much snappier than it used to be with moving around on the time slider and so forth.

At any rate, I'd appreciate any help with this. My machine's rather useable, it's just extremely annoying.

---

### Post by HiddenWolf on 2004-11-16
Do you have fam/gamin installed?

Are you using warty or hoary?

A lot of people reported sluggishness after the switch to hoary since they didn't install gamin instead of fam, as was the intention of the developers.

---

### Post by maus on 2004-11-16
[QUOTE=HiddenWolf]Do you have fam/gamin installed?

Are you using warty or hoary?

A lot of people reported sluggishness after the switch to hoary since they didn't install gamin instead of fam, as was the intention of the developers.[/QUOTE]

Hoary, upgraded from a Warty install from last month... aaand gamin solves the problem. Beauty. I was getting worried that I would have to live with waiting fifteen seconds for a right-click forever!

Oy, there's so much I need to learn about Gnome and X.

---

### Post by andy_sp1ke on 2004-11-16
i upgraded following the instructioins in the how to section from the i386 to i686 and my machine seems slower opening applications. I thought it should speed it up? I'm running a celeron CPU. How do I go back to the normal i386 to restore it with out losing everything on my machine?

Andy

---

### Post by jdong on 2004-11-16
sudo apt-get remove linux-686

---


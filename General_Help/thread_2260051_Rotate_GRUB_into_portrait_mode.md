---
title: "Rotate GRUB into portrait mode"
date: 2015-01-08
forum: General Help
---

### Post by DuckHook on 2015-01-08
All of my monitors are rotated into portrait mode. It is easy to set X into portrait mode and, with a little trouble, even *lightdm*. Since early 2014, it has also finally been possible to define:```
fbcon=rotate:3
```...which will rotate the console into portrait mode. \\:D/ This has been a godsend for those of us who still occasionally pretend to be console jockeys. The only remaining thorn is GRUB. Nothing I've found Googling tells me how to do it. Obviously, this is not important and is just an aesthetic thing, but for the sake of completeness and my inner geek, I'm wondering if anyone has ever managed it, or has any insights into how it might be done?

My gut tells me it is pretty much impossible. As far as I know, at the GRUB stage, no framebuffer has yet been loaded, the system is still in a very primitive state, and no mechanism exists at that point to pull off a trick like rotation. But I'm hoping that I'm wrong and it's just a setting that I'm ignorant of.

As always, all advice is greatly appreciated.

---

### Post by sudodus on 2015-01-09
I guess you have been browsing the internet for grub tutorials and grub manuals. I did some year ago (but not looking for rotating the grub menu). I do not remember anything about rotation, and I'm afraid you are right (and probably know more than I about it), that it is not possible. But let us hope there is someone who knows :-)

I think some monitors might be able to do the job (in the monitor settings, which is independent of the computer). Have you checked if that is possible with any of your monitors? I think this is also the case with some projectors, different rotation (but also mirror translations, which is useful when the audience is sitting on 'the other side' of the projection screen).

On the other hand, when I was a teacher very long ago, I learned to read upside down when helping the pupils. I think it is even easier to read text that is rotated only 90 degrees ;-)

---

### Post by DuckHook on 2015-01-09
Hi sudodus,

My monitors are all 12-yrs old, so very primitive settings and no rotation mode. But I'm wondering how a physical monitor could do this, even in theory? It would require switching the horizontal and vertical refresh alignments, clocks, rasters, as well as the EDID table, and I doubt that any manufacturer would go to that much technical trouble and expense for the sake of a few crazy oddballs like me who insist on a console in portrait mode. Far easier to just leave it to software.

It was just a lark anyway. 90° is no big deal. GRUB is only invoked for a few seconds at boot and my menu is pretty lean. My query was more in the spirit of hacking than of any real problem.

But after thinking about it some more, if one can customize GRUB with a background graphic, then surely some sort of framebuffer is being used. It then follows that the framebuffer can, at least in theory, be instructed to twist the output by 90°.

If all else fails (and I'm assuming that it will), I can always create a splash screen twisted 90° and load it at boot so that at least the background displays in portrait mode, but this is just cheating and offends my sense of propriety. Besides, it solves nothing if I have to actually get to the GRUB command line.

That's quite the trick to read upside down, especially for dynamic content. Speak like Yoda, did you it make?:D

---

### Post by sudodus on 2015-01-09
There was a monitor maybe 15 years ago, that you could twist (mechanically) between landscape and portrait mode. It was used by some secretaries in portrait mode to fit better the A4 paper format used in Europe. I thought the twist was done inside the monitor unit (and exchanging the generic width <---> height definition), but I'm not sure. Maybe it was just telling the operating system to twist the picture according to its physical twist position. I never checked what happened during boot :-P

---


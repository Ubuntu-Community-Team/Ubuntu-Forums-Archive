---
title: "Aptitude --not finding packages accessible through synaptic?"
date: 2005-08-30
forum: General Help
---

### Post by 5-HT on 2005-08-30
Hi,

 Not too sure why this is going on (or if it's a general issue or just specific) but when I was trying to download beep media player through aptitude, I could only find beep's development libraries for plugin composition and not the actual program itself; however, both synaptic and apt had no problems finding the player.

I'm not too familiar with aptitude, though would like to keep on using it for its advanced dependency handling abilities, and was wondering if anyone has any ideas as to why aptitude is not finding the beep player?

From what I believe aptitude and synaptic both use apt's sources list...so theoretically shouldn't the same packages be available regardless of whether you use aptitude/apt/synaptic?

Is anyone else having a problem like this for other packages?

Thanks for any ideas/help

---

### Post by Galoot on 2005-08-30
[QUOTE=5-HT]Is anyone else having a problem like this for other packages?[/QUOTE]I just finished installing it through aptitude without any problems after reading your post, so it sounds like a problem on your end. (I know this is of no help to you at all. Sorry.)

I'll step aside and let someone more knowlegable speak up.

---

### Post by 5-HT on 2005-08-30
[QUOTE=Galoot]I just finished installing it through aptitude without any problems after reading your post. [/quote]

Ha, well the good news is that it's not aptitude, so hopefully there's something that can be done.

I'll try using different repository mirrors (may work, but then if there was a problem with my sources list I'd expect both package managers to have the issue)

By the way though was Beep just called "beep-media-player" through aptitude (all I'm finding is "beep-media-player-dev"?

Thanks.

---

### Post by Galoot on 2005-08-30
[QUOTE=5-HT]By the way though was Beep just called "beep-media-player" through aptitude (all I'm finding is "beep-media-player-dev"?

Thanks.[/QUOTE]
It was called beep-media-player. Both it and beep-media-player-dev were listed.

Probably a useless suggestion, but did you try (u)pdating your package list?

---

### Post by 5-HT on 2005-08-30
Yeah, tried a bunch of times.

Actually I messed up my partition sizes during the original installation and had to reformat and reinstall ubuntu completely and I do remember that I couldn't find beep through aptitude then either.

I think i'm hitting all the repositories in my sources list as I get the green tabs in aptitude when updating (and synaptic gives no errors).

---

### Post by 5-HT on 2005-08-31
I'm thinking that this is a larger issue than what it initially appeared to be.

I'm now having the same issue with 'mtink' as well as a few other packages that I can find through synaptic.

I did make one discovery though...If I use aptitude from the command line, I can find all the packages, whereas through the GUI it looks like a lot of programs can not be found, though their doc files and 'add-ons' can be (for example through aptitude's GUI I found only 'mtink-doc', though from the command line I could find both 'mtink' and 'mtink-doc').

Looks like I may be the only one having this issue, but was wondering if anyone has experienced this or has any ideas about how to resolve it?

---

### Post by Galoot on 2005-08-31
[QUOTE=5-HT]was wondering if anyone has experienced this or has any ideas about how to resolve it?[/QUOTE]
Does anyone know if aptitude keeps its own database?

The reason I ask is that I once solved the seemingly unrelated "*aptitude-will-uninstall-damned-near-everything-even-though-you-don't-want-it-to*" problem by exiting out, purging the aptitude program itself using Synaptic, then reinstalling it with Synaptic.

I don't know if this would solve your problem--or if it's even a sane solution to *my* problem--but it did get things working right for me again.

---


---
title: "Ubuntu, Firefox, and fonts"
date: 2008-02-07
forum: General Help
---

### Post by Beretta_NZ on 2008-02-07
Today is my first day with Ubuntu. I installed it on my laptop last night.

This is the first strange thing that has happened. After installing Ubuntu, I wanted to have a few extra fonts, so I installed some funky ttf fonts. No problem, they all work fine.

Then I opened my firefox Browser, and what the? Regular text is displaying in one of my new fonts, making pages very hard to read. It looks like this:
[ATTACH]59036[/ATTACH]
Now, I'm able to get around this, by using the following, under Edit > Preferences > Content > Advanced:
[ATTACH]59037[/ATTACH]

If I de-select that option, and prevent websites from determining the font, then I can use the default fonts. The trouble is that this prevents some websites from displaying as they should.

Another person here reported a similar problem, and the solution given to them was to type about:config and change layout.css.dpl to 0. Well, I tried that, but even with the new value there and firefox restarted, the problem persists. Are there any other ideas why might cause this and how to remedy it?

Many thanks in advance.

---

### Post by strabes on 2008-02-07
Try making a new firefox profile by running ```
firefox -profilemanager
```

If the problem persists, try removing those extra fonts that you installed.

---

### Post by Beretta_NZ on 2008-02-08
Hey, thanks so much strabes.

The profile manager did not seem to change anything. Removing the font did stop firefox from automatically using it, but the only problem is that I can now never use the font. I hope this doesn't happen with other fonts I try to add.

---

### Post by Beretta_NZ on 2008-02-08
OK,this might help someone out there to see what's causing this.

I just upgraded to the latest Ubuntu, and reinstalled all my fonts - the same problem is occurring. But here's something else I noticed - in Pigdin instant messenger, incoming messages are also appearing in that same funky font. I can stop this in the settings, by removing all formatting from incoming messages, but it looks like there's some universal setting here (i.e. not specific to firefox) that's causing this.

Does anyone know what it might be?

---

### Post by lswest on 2008-02-08
try checking the system fonts, maybe something changed it from Sans? (under, i think, system-->preferences-->appearance) or so, not entirely sure where the fonts can be chosen (not on a linux PC atm)

---

### Post by Beretta_NZ on 2008-02-09
Thanks Iswest. I had a look there, and all the fonts set there are just regular fonts, not this funky one that keeps appearing.

This has me stumped.

---

### Post by Beretta_NZ on 2008-02-10
Man, this is driving me nuts. I've just installed Google Earth, and it's using the same whacked out font! There's a hidden universal setting SOMEwhere that I just don't know about.

---

### Post by Beretta_NZ on 2008-02-10
OK, I just deleted the font from my system. An imperfect solution, but I had to do something.

---

### Post by Beretta_NZ on 2008-02-10
OK.... now I have just installed Wine, and that is displaying with a different one of my unusual fonts! There has to be a setting for this, but I just can't find one.

---

### Post by Beretta_NZ on 2008-02-10
Wait, cancel that. Wine needs the desired fonts put into its font folder, which I've done now, and all is well.

---


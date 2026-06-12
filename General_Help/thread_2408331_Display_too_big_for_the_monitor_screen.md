---
title: "Display too big for the monitor screen"
date: 2018-12-17
forum: General Help
---

### Post by Richard_York on 2018-12-17
Hello, I recently had great help here to sort out a problem with screen display  with Ubuntu18LTS and a Samsung Syncmaster 172v monitor. The most relevant information is perhaps at posts #12 and #16 on
[https://ubuntuforums.org/showthread.php?t=2406693&page=2](https://ubuntuforums.org/showthread.php?t=2406693&page=2)

Now things are legible rather than distorted, and the cursor stops at all four edges of the screen. 

But the display is still somewhat oversized. To view things like "pay now" boxes on websites we have to use  CTRL -     to bring such items back into view.
While that works, each & every web page we look at needs shrinking to view properly, and every Libre Office and other document we work on offline is also a bit too "in your face" for comfort.

How can I shrink the display and keep it that way, please?

While online checking gave me the supposed resolution for this monitor, quoted in the thread I linked to, I've since noticed that various sites quote various figures for what it should be, which doesn't help.

Thanks.

---

### Post by CatKiller on 2018-12-17
You could try ```
gsettings set org.gnome.desktop.interface scaling-factor 1
```

---

### Post by Richard_York on 2018-12-17
Thanks 
I tried copying & pasting this in. It didn't appear to have any results. The Terminal just accepted it and waited for the next command without response. I have realised, however, that I can set Firefox to 80% zoom, however, which seems sometimes to stick and sometimes not, but saves having to adjust each page we look at.

---

### Post by CatKiller on 2018-12-17
Hmm. That's a shame. I was hoping that Gnome's HiDPI scaling had got enabled by mistake. That would have given the symptoms you've seen of the display being at the right resolution, but things being displayed too big.

Maybe there's a different setting for that somewhere. I don't use Gnome, so I can't check. 

I'm out of ideas. Hopefully someone else can come up with something.

---

### Post by Richard_York on 2018-12-29
Thanks anyway!

---

### Post by raul-mccai on 2018-12-29
did you try CTL and 0 ??

---

### Post by Richard_York on 2019-01-01
Thanks: I tried CTRL and  0, yes, (unless you mean something different here) and it keeps it looking  a bit too big. We've currently got Firefox set on 80% viewing size, (CTRL and - twice over) and that makes things workable most of the time. But of course, only with Firefox.

---

### Post by dragonfly41 on 2019-01-01
Toggle various display modes using [SuperKey]+[P] (SuperKey is the one with a Windows icon).
I think the toggle cycle is 3 to go through 3 modes.
I'm not sure what it does, mind you, but I have to do this black magic every time I boot up.
One day I'll find the gnome tweak.

---

